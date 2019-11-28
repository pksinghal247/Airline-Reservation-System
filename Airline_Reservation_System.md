# Airline-Reservation-System
PK airline Reservation System have 10 seats 5 for First class and 5 for Executive class. Code is written in Java
## Happy Coding :)
```java
import java.io.Console;

import jdk.nashorn.internal.ir.JumpStatement;

class Ticket
{
    private static int c1=0, c2=5;
    String[] flightSeats = new String[10];                                                    // Array of Seats
    public Ticket()
    {
        for (int i = 0; i < 10; i++) 
        {
            this.flightSeats[i] = "Available";    
        }
    }
    public void checkFlight()
    {   
        header();
        System.out.print((char)27 + "[31m" +"\n\n\t\t\t\t\t First Class Availability : ");
        System.out.println("\t\tEconomy Class Availability : "+ (char)27 + "[0m");
        System.out.print("\n\t\t\t\t\t*******************************");
        System.out.println("\t\t*******************************");
        System.out.print("\t\t\t\t\t Seat No.\tAvailability");
        System.out.println("\t\t Seat No.\tAvailability");
        System.out.print("\t\t\t\t\t*******************************");
        System.out.println("\t\t*******************************");
        
        for (int ele = 0; ele < 5; ele++) 
        {
			if (flightSeats[ele] == "Booked") 
			{
				System.out.print("\t\t\t"+(char)27 + "[31m\t\t  " + (ele+1)+"\t\t"+flightSeats[ele] + (char)27 + "[0m\t");
			} 
			else 
			{
				System.out.print("\t\t\t\t\t  "+(ele+1)+"\t\t"+flightSeats[ele]);	
			}    
			if (flightSeats[ele+5] == "Booked") 
			{
				System.out.print((char)27 + "[31m\t\t  " + (ele+6)+"\t\t"+flightSeats[ele+5] + (char)27 + "[0m");
			} 
			else 
			{
				System.out.print("\t\t  "+(ele+6)+"\t\t"+flightSeats[ele+5]);	
			}    
			System.out.println();
        }
        System.out.print("\t\t\t\t\t-------------------------------");
		System.out.println("\t\t-------------------------------");
	}
    public void bookSeat()                                                                          // Function for booking a seat in reservtion system
    {
        header();
        System.out.println("\n\n\t\t\t\t\t\t\tEnter FC for First Class. \n\t\t\t\t\t\t\tEnter EC for Economy Class.");         //Asks user for his preffered class to travel
        String passengerClass = System.console().readLine((char)27 + "[31m\t\t  " + "\n\n\t\t\t\t\t\t\tEnter Your Choice..? "+ (char)27 + "[0m").toLowerCase();
        switch(passengerClass)
        {
            case "fc":
                firstClassBooking();
                break;
            case "ec":
                economyClassBooking();
                break;
            default:
                System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\t\t\t!!!.....Invalid Class.....!!!"+ (char)27 + "[0m");
        }
    }

    public void firstClassBooking()                                                                  // Check and book for first class seating
    {
        for ( int cnt = 0; cnt < 5; cnt++ )
        {
            if ( flightSeats[cnt] == "Available" )                                                        //check if seat is available to allocate to user booking.
            {
                flightSeats[cnt] = "Booked";
                c1++;                                                            //book seat
                header();
                boardingPass(cnt+1);
                break;
            }
            else if ( flightSeats[4] == "Booked" && flightSeats[9] == "Booked")
            {
                header();
                System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\tApologies!! All seats are booked. Next flight is scheduled in next 3 hours...");
                break;
            }
            else if( flightSeats[4] == "Booked" )                                                                               // provide passenger another available class option
            {
                header();
                System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\tSorry,First Class bookings are over. Would you like to opt for Economy class ? ");  
                System.out.println("\n\t\t\t\t\t\t\tEnter Y for yes.\n\t\t\t\t\t\t\tEnter N for no.");
                String selection = System.console().readLine("\n\t\t\t\t\t\t\t Enter Your Choice ? ").toLowerCase();
                switch (selection) 
                {
                    case "y":
                        economyClassBooking();
                        break;
                    case "n":
                        System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\t\t\tNext flight is scheduled in '3' hours.");
                        break;
                    default:
                        System.out.println((char)27 + "[31m" +"\n\t\t\t\t\t\t\t!!!.....Invalid Selection.....!!!");
                        break;
                }
                break;
            }
        }
    }       

    public void economyClassBooking()                                                       // Check and book for economy class seating
    {
        for ( int cnt = 5; cnt < 10; cnt++ )
        {
            if ( flightSeats[cnt] == "Available" )
            {
                flightSeats[cnt] = "Booked";
                c2++;
                header();
                boardingPass(cnt+1);
                break;
            }
            else if ( flightSeats[9] == "Booked" && flightSeats[4] == "Booked")
            {
                header();
                System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\tApologies!! All seats are booked. Next flight is scheduled in '3' hours.");
                break;
            }    
            else if (flightSeats[9] == "Booked")
            {   
                header();
                System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\tSorry, Economy Class bookings are over. Would you like to opt for first class ? "); 
                System.out.println("\n\t\t\t\t\t\t\tEnter Y for yes.\n\t\t\t\t\t\t\tEnter N for no.");
                String selection = System.console().readLine("\n\t\t\t\t\t\t\t Enter Your Choice ? ").toLowerCase();
                switch (selection) 
                {
                    case "y":
                        firstClassBooking();
                        break;
                    case "n":
                        System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\t\t\tNext flight is scheduled in '3' hours.");
                        break;
                    default:
                        System.out.println((char)27 + "[31m" +"\n\t\t\t\t\t\t\t!!!.....Invalid Selection.....!!!");
                        break;     
                }
                break;
            }
        }
    }
 

    public void header() 
    {
        System.out.print("\033[H\033[2J");
        System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\t\t*************************************************");
    	System.out.println("\t\t\t\t\t\t| Airline Reservations System BY Praful Singhal |");
        System.out.println("\t\t\t\t\t\t*************************************************"+ (char)27 + "[0m");
        System.out.println("\n\n\t\t\t\t\t\t\tPK Airlines : High class, low fares.");
    }

    public void boardingPass(int seat)                                      // Generate Boarding Pass
    {
        header();
        System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\t\t\t********************************************");
        System.out.println((char)27 + "[31m" +"\t\t\t\t\t\t\t|\t\t PK Airlines\t\t   |");
        System.out.println((char)27 + "[31m" +"\t\t\t\t\t\t\t|\t\tBoarding Pass\t\t   |");
        if (seat >0 && seat < 11) 
        {
            if (seat <= c1) 
            {
                System.out.printf((char)27 + "[31m" +"\t\t\t\t\t\t\t|\t\t\t\t\t   |\n\t\t\t\t\t\t\t|  First Class  \t\tSeat# %d\t   |\n", seat);
                System.out.println((char)27 + "[31m" +"\t\t\t\t\t\t\t********************************************");
            } 
            else
            {
                if (seat > 5 && seat <= c2) 
                {
                    System.out.printf((char)27 + "[31m" +"\t\t\t\t\t\t\t|\t\t\t\t\t   |\n\t\t\t\t\t\t\t|  Economy Class\t\tSeat:%d\t   |\n", seat);
                    System.out.println((char)27 + "[31m" +"\t\t\t\t\t\t\t********************************************");
                }  
                else
                {
                    header();
                    System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\t\t\t!!!.....Seat Not Booked.....!!!");
                    
                }               
            }
        } 
        else 
        {
            header();
            System.out.println((char)27 + "[31m" +"\n\n\t\t\t\t\t\t\t!!!.....Seat Not Found.....!!!"+ (char)27 + "[0m");
        }
        
    }

    public void printBoarding() 
    {
        header();
        int seat = Integer.parseInt(System.console().readLine("\n\n\t\t\t\t\t\t\tEnter Seat Number    :  "));
        boardingPass(seat);
    }

    public void reset()
    {
        for (int ele = 0; ele < 10; ele++) 
        {
            flightSeats[ele] = "Available";   
        }
        c1=0;
        c2=0;
        header();
        System.out.println((char)27 + "[31m" +"\n\n\n\t\t\t\t\t\tLast Flight is Departed. Booking allowed in next flight Onwards... "+ (char)27 + "[0m");
    } 
};   


class Airline
{
    public static void main(String[] args) 
    {
        Ticket passenger = new Ticket();
        int ch = 0;
        while (true) 
        {
            System.console().readLine("\n\n\t\t\t\t\t\t\tPress Enter to  Continue.....!!!");
            passenger.header();
            System.out.println("\n\n\t\t\t\t\t\t\tEnter 1 to Book Ticket.\n\t\t\t\t\t\t\tEnter 2 to Display Seats.\n\t\t\t\t\t\t\tEnter 3 to Print Boarding Pass.\n\t\t\t\t\t\t\tEnter 4 to Book in Next Flight.\n\t\t\t\t\t\t\tEnter 5 to Exit.");
            ch = Integer.parseInt(System.console().readLine((char)27 + "[31m" +"\n\n\t\t\t\t\t\t\tEnter Your Choice..? "+ (char)27 + "[0m"));
            switch(ch)
            {
                case 1:
                    passenger.bookSeat();
                    break;
                case 2:
                    passenger.checkFlight();
                    break;
                case 3:
                    passenger.printBoarding();
                    break;    
                case 4:
                    passenger.reset();
                    break;
                case 5:
                    System.out.print("\033[H\033[2J");
                    System.out.println("\n\n\n\n\n\n\n\n\n\n\n\n\n\n\t\t\t\t\t\tThank You For Using PK Airline Reservation System.....\n\n\n\n\n\n\n\n\n\n\n\n\n\n\n");
                    System.exit(0);
                default:
                    System.out.println((char)27 + "[31m" +"\t\t\t\t\t\t\t!!!.....Invalid Selection.....!!!");
                    break;            
            }
        }
        
   }
};
```
