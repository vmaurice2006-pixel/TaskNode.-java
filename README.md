import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

class Customer {
    private String name;
    private int number;

    public Customer(String name, int number) {
        this.name = name;
        this.number = number;
    }

    public String getName() {
        return name;
    }

    public int getNumber() {
        return number;
    }

    @Override
    public String toString() {
        return "Customer{" +
                "name='" + name + '\'' +
                ", number=" + number +
                '}';
    }
}

public class BankQueue {
    public static void main(String[] args) {
        Queue<Customer> queue = new LinkedList<>();
        Scanner scanner = new Scanner(System.in);
        int customerNumber = 1;

        while (true) {
            System.out.println("1. Add customer to queue");
            System.out.println("2. Serve next customer");
            System.out.println("3. View queue");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter customer name: ");
                    String name = scanner.nextLine();
                    Customer customer = new Customer(name, customerNumber++);
                    queue.offer(customer);
                    System.out.println("Customer added to queue.");
                    break;
                case 2:
                    if (!queue.isEmpty()) {
                        Customer servedCustomer = queue.poll();
                        System.out.println("Serving customer: " + servedCustomer.getName() +
                                " with number " + servedCustomer.getNumber());
                    } else {
                        System.out.println("No customers in the queue.");
                    }
                    break;
                case 3:
                    if (queue.isEmpty()) {
                        System.out.println("Queue is empty.");
                    } else {
                        System.out.println("Current queue: " + queue);
                    }
                    break;
                case 4:
                    System.out.println("Exiting...");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
            System.out.println();
        }
    }
}

