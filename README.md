# Real-Time Chat Application

## Project Overview
This project is a real-time chat application built using Node.js, Express, MongoDB, and Socket.io. The application supports user authentication, chat room creation, real-time messaging, push notifications, and file uploads. A pivot collection (`UserRoom`) is used to efficiently manage the many-to-many relationship between users and chat rooms.

## Features
- **User Authentication:** Register and log in with JWT-based authentication.
- **Chat Rooms:** Create, join, and view a list of chat rooms.
- **Real-Time Messaging:** Send and receive messages in real-time within chat rooms.
- **Push Notifications:** Simulated server-side notifications for new messages in chat rooms.
- **File Upload:** Upload and share files in chat rooms.
- **Logging:** Integrated logging with Winston to capture events and errors.
- **Testing:** Comprehensive test coverage using Mocha, Chai, and Supertest.

## Project Structure

chat-app/
│
├── config/
│ ├── db.js # Database connection setup
│ └── logger.js # Logger configuration
│
├── controllers/
│ ├── authController.js # Handles authentication requests
│ └── chatController.js # Manages chat-related requests and file uploads
│
├── services/
│ ├── authService.js # Contains business logic for authentication
│ └── chatService.js # Contains business logic for chat operations and notifications
│
├── models/
│ ├── User.js # User model schema
│ ├── Room.js # Chat room model schema
│ └── UserRoom.js # Pivot collection schema for user-room mapping
│
├── routes/
│ ├── authRoutes.js # Authentication routes
│ └── chatRoutes.js # Chat-related routes including file upload
│
├── middleware/
│ ├── authMiddleware.js # Middleware to protect routes with JWT authentication
│ └── uploadMiddleware.js # Middleware to handle file uploads using multer
│
├── events/
│ ├── eventEmitter.js # EventEmitter setup for handling events
│ └── notificationEvents.js # Handles notification-related events
│
├── test/
│ ├── auth.test.js # Test cases for authentication
│ └── chat.test.js # Test cases for chat functionality and file uploads
│
├── uploads/ # Directory where uploaded files are stored
│
├── server.js # Main server setup file
├── package.json # Project dependencies and scripts
└── .env # Environment variables (e.g., JWT secret, DB URI)

## Installation and Setup

### Prerequisites
- Node.js (v14.x or higher)
- MongoDB (running locally or on a server)
- npm (Node Package Manager)

### Installation

1. Clone the repository:

   git clone https://github.com/yourusername/chat-app.git
   cd chat-app

2. Install dependencies:
    npm install

3. Set up environment variables:
    Create a .env file in the root directory with the following content

        MONGO_URI=mongodb://localhost:27017/chat-app
        JWT_SECRET=your_jwt_secret

    Replace your_jwt_secret with a strong secret key.

4. Start the MongoDB server if it's not already running:
    mongod

5. Start the Node.js server:
    npm start

6. The server will start on http://localhost:5000.

Running Tests:

To run the test suite, use the following command:
    npm test

API Endpoints
    Authentication
        POST /api/auth/register: Register a new user.
        POST /api/auth/login: Log in an existing user.
    Chat Rooms
        POST /api/chat/room: Create a new chat room.
        GET /api/chat/rooms: List all chat rooms for the authenticated user.
        GET /api/chat/room/:roomId/users: List users in a chat room.
        POST /api/chat/room/:name/join: Join a chat room.
        POST /api/chat/room/:name/message: Send a message in a chat room.
        POST /api/chat/room/:name/upload: Upload a file to a chat room.
        GET /api/chat/room/:name/history: Get the chat history for a room.