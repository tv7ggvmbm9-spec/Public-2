# Public-2
java wishlist
import java.util.ArrayList;
import java.util.Scanner;

public class TravelWishlist {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        ArrayList<String> wishes = new ArrayList<>();

        System.out.println("L+O World travel — Customer Wish List");
        System.out.print("Customer name: ");
        String customer = input.nextLine();

        while (true) {
            System.out.println("\n1. Add a travel wish");
            System.out.println("2. View wish list");
            System.out.println("3. Mark a wish as planned");
            System.out.println("4. Exit");
            System.out.print("Choose: ");
            String choice = input.nextLine().trim();

            switch (choice) {
                case "1":
                    System.out.print("Dream experience or destination: ");
                    String wish = input.nextLine().trim();

                    if (!wish.isEmpty()) {
                        wishes.add("[To plan] " + wish);
                        System.out.println("Wish added!");
                    }
                    break;

                case "2":
                    System.out.println("\nTravel wishes for " + customer);

                    if (wishes.isEmpty()) {
                        System.out.println("No wishes yet.");
                    }

                    for (int i = 0; i < wishes.size(); i++) {
                        System.out.println((i + 1) + ". " + wishes.get(i));
                    }
                    break;

                case "3":
                    System.out.print("Wish number to mark as planned: ");

                    try {
                        int index = Integer.parseInt(input.nextLine()) - 1;

                        if (index >= 0 && index < wishes.size()) {
                            String updated = wishes.get(index)
                                .replace("[To plan]", "[Planned]");
                            wishes.set(index, updated);
                            System.out.println("Wish marked as planned!");
                        } else {
                            System.out.println("That wish number doesn't exist.");
                        }
                    } catch (NumberFormatException e) {
                        System.out.println("Please enter a number.");
                    }
                    break;

                case "4":
                    System.out.println("Thank you for choosing L+O World travel!");
                    input.close();
                    return;

                default:
                    System.out.println("Please choose 1, 2, 3, or 4.");
            }
        }
    }
}
