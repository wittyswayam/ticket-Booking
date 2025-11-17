# Train Ticket Booking System

A Java-based command-line application for managing train ticket bookings with user authentication, seat selection, and booking management features.

## Features

- **User Authentication**
  - Secure user signup with password hashing (BCrypt)
  - User login with credential verification
  
- **Train Management**
  - Search trains by source and destination stations
  - View available trains with station timing information
  - Real-time seat availability display

- **Booking System**
  - Book seats on available trains
  - View all user bookings
  - Cancel existing bookings
  - Seat matrix visualization (4x6 seating layout)

## Technology Stack

- **Java 8**
- **Gradle 8.5** - Build tool
- **Jackson 2.12.6** - JSON serialization/deserialization
- **BCrypt 0.4** - Password hashing
- **Lombok 1.18.22** - Code generation
- **JUnit 4.13.2** - Testing framework

## Project Structure

```
ticket-booking/
├── app/
│   ├── src/
│   │   ├── main/
│   │   │   └── java/
│   │   │       └── ticket/booking/
│   │   │           ├── entities/
│   │   │           │   ├── Train.java
│   │   │           │   ├── User.java
│   │   │           │   └── Ticket.java
│   │   │           ├── service/
│   │   │           │   ├── TrainService.java
│   │   │           │   └── UserBookingService.java
│   │   │           ├── util/
│   │   │           │   └── UserServiceUtil.java
│   │   │           ├── localDB/
│   │   │           │   ├── trains.json
│   │   │           │   └── users.json
│   │   │           └── App.java
│   │   └── test/
│   └── build.gradle
├── gradle/
├── gradlew
├── gradlew.bat
└── settings.gradle
```

## Prerequisites

- Java Development Kit (JDK) 8 or higher
- Gradle 8.5 (or use included Gradle wrapper)


## Usage

The application provides an interactive command-line menu with the following options:

### 1. Sign Up
- Create a new user account
- Enter username and password
- Password is securely hashed before storage

### 2. Login
- Authenticate with existing credentials
- Access personalized booking features

### 3. Fetch Bookings
- View all your current ticket bookings
- Display ticket details including train info, source, destination, and travel date

### 4. Search Trains
- Enter source station
- Enter destination station
- View available trains with timing information

### 5. Book a Seat
- Select a train from search results
- View seat availability matrix (0 = available, 1 = booked)
- Choose seat by row and column
- Confirm booking

### 6. Cancel Booking
- Enter ticket ID to cancel
- Booking will be removed from your account

### 7. Exit
- Close the application

## Data Storage

The application uses JSON files for data persistence:

- **users.json** - Stores user accounts and booking history
- **trains.json** - Contains train information, routes, and seat availability

## Security

- Passwords are hashed using BCrypt with salt
- Plain text passwords are never stored
- Authentication required for booking operations

## Example Workflow

1. **Sign up** with username and password
2. **Login** to access the system
3. **Search trains** from "bangalore" to "delhi"
4. **Select a train** from the results
5. **View seat matrix** and choose an available seat
6. **Book the seat** and receive confirmation
7. **Fetch bookings** to verify your reservation

## Data Models

### User
- Username
- Hashed password
- List of booked tickets
- Unique user ID

### Train
- Train ID and number
- Seat matrix (4 rows x 6 columns)
- Station-time mappings
- Station sequence

### Ticket
- Ticket ID
- User ID
- Source and destination
- Date of travel
- Associated train details

## Development

### Running Tests
```bash
./gradlew test
```

### Building JAR
```bash
./gradlew jar
```

### Clean Build
```bash
./gradlew clean build
```
## Known Issues

- Train data file path is relative and may need adjustment based on execution context
- Case sensitivity in station names (recommend lowercase input)
- Limited error handling for invalid user inputs

## Future Enhancements

- Database integration (MySQL/PostgreSQL)
- REST API implementation
- Web-based user interface
- Payment gateway integration
- Real-time train tracking
- Email notifications
- Multi-class seating options
- Waitlist management
