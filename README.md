# Ap-3-assignment-


Draw uml class diagram for library management system that includes book member and librarian class  with relationship like aggregation and inheritance


// Book Class: Represents a book in the library.
class Book {
    private String title;
    private String author;
    private String isbn;

    public Book(String title, String author, String isbn) {
        this.title = title;
        this.author = author;
        this.isbn = isbn;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public String getIsbn() {
        return isbn;
    }

    @Override
    public String toString() {
        return "Book[Title=" + title + ", Author=" + author + ", ISBN=" + isbn + "]";
    }
}

// Member Class: Represents a library member (could be any member).
class Member {
    private String name;
    private String memberId;

    public Member(String name, String memberId) {
        this.name = name;
        this.memberId = memberId;
    }

    public String getName() {
        return name;
    }

    public String getMemberId() {
        return memberId;
    }

    public void borrowBook(Book book) {
        System.out.println(name + " borrowed the book: " + book.getTitle());
    }

    public void returnBook(Book book) {
        System.out.println(name + " returned the book: " + book.getTitle());
    }
}

// Librarian Class: Inherits from Member Class (Inheritance)
class Librarian extends Member {
    private String employeeId;

    public Librarian(String name, String memberId, String employeeId) {
        super(name, memberId);
        this.employeeId = employeeId;
    }

    public String getEmployeeId() {
        return employeeId;
    }

    public void manageLibrary() {
        System.out.println(getName() + " is managing the library.");
    }

    public void addBookToLibrary(Book book) {
        System.out.println(getName() + " added book: " + book.getTitle() + " to the library.");
    }
}

// Library Class: Aggregates Books and Members
class Library {
    private Book[] books;
    private Member[] members;

    public Library(int bookCapacity, int memberCapacity) {
        books = new Book[bookCapacity];
        members = new Member[memberCapacity];
    }

    public void addBook(Book book, int index) {
        books[index] = book;
    }

    public void addMember(Member member, int index) {
        members[index] = member;
    }

    public void showLibraryDetails() {
        System.out.println("Books in the Library:");
        for (Book book : books) {
            if (book != null) {
                System.out.println(book);
            }
        }

        System.out.println("Members in the Library:");
        for (Member member : members) {
            if (member != null) {
                System.out.println(member.getName() + " (" + member.getMemberId() + ")");
            }
        }
    }
}

// Main Class to test the program
public class LibraryManagementSystem {
    public static void main(String[] args) {
        // Create Books
        Book book1 = new Book("Java Programming", "John Doe", "12345");
        Book book2 = new Book("Python Basics", "Jane Smith", "67890");

        // Create Members
        Member member1 = new Member("Alice", "M001");
        Member member2 = new Member("Bob", "M002");

        // Create Librarian
        Librarian librarian = new Librarian("Charlie", "L001", "E123");

        // Create Library and add books and members
        Library library = new Library(5, 5);
        library.addBook(book1, 0);
        library.addBook(book2, 1);
        library.addMember(member1, 0);
        library.addMember(member2, 1);
        library.addMember(librarian, 2);

        // Show Library Details
        library.showLibraryDetails();

        // Librarian manages the library
        librarian.manageLibrary();
        librarian.addBookToLibrary(new Book("C++ Programming", "George Brown", "11111"));

        // Member borrows and returns books
        member1.borrowBook(book1);
        member2.borrowBook(book2);
        member1.returnBook(book1);
    }
}
