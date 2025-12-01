# TaskManager Backend

> Express.js REST API backend for TaskManager. Handles authentication, task management, and MongoDB database operations with JWT-based security.

**Deployed on:** Render (Node.js Web Service)

---

## Table of Contents
- [About](#about)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Frontend Repository](#frontend-repository)
- [Author](#author)
- [Support](#support)

---

## About

TaskManager Backend is a **Node.js/Express REST API** that provides:

- Secure user authentication with JWT tokens  
- Full CRUD operations for tasks  
- MongoDB database integration with Mongoose  
- CORS support for cross-origin requests from React frontend  
- Production-ready error handling and validation  

This backend powers the [TaskManager](https://github.com/vishal-singh-web/TaskManager) full-stack application.

---

## Features

✅ **User Authentication**
- JWT-based login and signup  
- Password encryption with bcryptjs  
- Protected routes with authentication middleware  

✅ **Task Management**
- Create, read, update, delete tasks  
- User-specific task isolation  
- Validation and error handling  

✅ **Database**
- MongoDB Atlas integration  
- Mongoose schema validation  
- Efficient query operations  

✅ **Security**
- CORS enabled for frontend requests  
- Environment variables for sensitive data  
- Input validation on all endpoints  

---

## Tech Stack

- **Node.js** – JavaScript runtime  
- **Express.js** – Web framework  
- **MongoDB Atlas** – Cloud database  
- **Mongoose** – ODM for MongoDB  
- **JWT (jsonwebtoken)** – Authentication tokens  
- **bcryptjs** – Password hashing  
- **CORS** – Cross-origin resource sharing  
- **dotenv** – Environment variable management  

---

## Getting Started

### Prerequisites

- Node.js (v14+) installed  
- npm package manager  
- MongoDB Atlas account (free tier)  
- Git for version control  

### Installation

1. **Clone the repository:**
git clone https://github.com/vishal-singh-web/taskmanager-backend.git
cd taskmanager-backend



2. **Install dependencies:**
npm install



3. **Create `.env` file** in root directory:
PORT=5000
MONGODB_URI=mongodb+srv://username:password@cluster0.mongodb.net/taskmanager?retryWrites=true&w=majority
JWT_SECRET=your_jwt_secret_key_here
NODE_ENV=development
CORS_ORIGIN=http://localhost:3000



4. **Start the server:**
npm start



Server runs at:  
`http://localhost:5000`

For development with auto-reload (if `nodemon` is set up):
npm run dev



---

## Environment Variables

Create a `.env` file in the root directory:

PORT=5000
MONGODB_URI=mongodb+srv://username:password@cluster0.mongodb.net/taskmanager?retryWrites=true&w=majority
JWT_SECRET=your_secret_key_here
NODE_ENV=development
CORS_ORIGIN=http://localhost:3000



**Important:**
- Never commit `.env` to Git.  
- Add it to `.gitignore`:
.env
.env.local



---

## API Endpoints

### Base URL (Local)

http://localhost:5000



(Replace with your Render URL in production, e.g. `https://taskmanager-backend.onrender.com`)

---

### Authentication Routes

#### POST /api/auth/signup

- **Description:** Register a new user  
- **Request Body:**
{
"name": "John Doe",
"email": "john@example.com",
"password": "password123"
}


- **Response:**
{
"token": "jwt_token_here",
"user": {
"_id": "user_id",
"name": "John Doe",
"email": "john@example.com"
}
}



#### POST /api/auth/login

- **Description:** Login with email and password  
- **Request Body:**
{
"email": "john@example.com",
"password": "password123"
}


- **Response:**
{
"token": "jwt_token_here",
"user": {
"_id": "user_id",
"name": "John Doe",
"email": "john@example.com"
}
}



---

### Task Routes (Protected – Requires JWT Token)

All task routes require the header:  
`token: <token>`

#### GET /api/fetchtasks

- **Description:** Fetch all tasks for logged-in user  
- **Response:**
[
{
"_id": "task_id",
"title": "My Task",
"description": "Task description",
"createdAt": "2025-01-01T00:00:00.000Z",
"userId": "user_id"
}
]



#### POST /api/addtask

- **Description:** Create a new task  
- **Request Body:**
{
"title": "New Task",
"description": "Task description",
"status":"Task status",
"priority":"Task priority"
}


- **Response:**
{
"_id": "task_id",
"title": "New Task",
"description": "Task description",
"status":"Task status",
"priority":"Task priority"
"createdAt": "2025-01-01T00:00:00.000Z",
"userId": "user_id"
}



#### PUT /api/tasks/:id

- **Description:** Update an existing task  
- **Request Body:**
{
"title": "Updated Task",
"description": "Updated description",
"status":"Updated status",
"priority":"Updated priority"
}


- **Response:**
{
"_id": "task_id",
"title": "Updated Task",
"description": "Updated description",
"status":"Updated status",
"priority":"Updated priority",
"updatedAt": "2025-01-01T00:00:00.000Z",
"userId": "user_id"
}



#### DELETE /api/tasks/:id

- **Description:** Delete a task  
- **Response:**
{
"message": "Task deleted successfully"
}



---

## Project Structure
```
taskmanager-backend/
├── routes/
│ ├── auth.js # Authentication endpoints
│ └── tasks.js # Task CRUD endpoints
├── models/
│ ├── User.js # User schema
│ └── Task.js # Task schema
├── middleware/
│ └── auth.js # JWT verification middleware
├── index.js # Server entry point
├── package.json # Dependencies & scripts
├── .env # Environment variables (not committed)
└── README.md # This file
```

---

## Deployment

### Deploy on Render

1. **Push code to GitHub:**
git add .
git commit -m "Initial backend commit"
git push origin main


2. **On Render:**
- Go to [https://render.com](https://render.com)  
- Click **“New” → “Web Service”**  
- Connect your GitHub repository  
- **Environment:** Node  
- **Build Command:** `npm install`  
- **Start Command:** `npm start`  
- Add environment variables: `MONGODB_URI`, `JWT_SECRET`, `PORT` (optional), `CORS_ORIGIN`  
- Click **“Create Web Service”**

3. **Get your backend URL**, e.g.:  
`https://taskmanager-backend.onrender.com`

4. **Update frontend `.env`** with this URL:
REACT_APP_API_URL=https://taskmanager-backend.onrender.com



---

## Contributing

Contributions are welcome! Follow these steps:

1. Fork the repository  
2. Create a feature branch:
git checkout -b feature/NewFeature


3. Commit your changes:
git commit -m "Add NewFeature"


4. Push to the branch:
git push origin feature/NewFeature


5. Open a Pull Request

---

## License

This project is **not licensed**.  
All rights reserved by the author.

---

## Frontend Repository

**TaskManager Frontend:**  
[https://github.com/vishal-singh-web/TaskManager](https://github.com/vishal-singh-web/TaskManager)

---

## Author

**Vishal Singh**  
- GitHub: [@vishal-singh-web](https://github.com/vishal-singh-web)  
- LinkedIn: [ https://www.linkedin.com/in/vishalsingh-profile]( https://www.linkedin.com/in/vishalsingh-profile/)

---

## Support

Have questions or found an issue?  
[Open an Issue](https://github.com/vishal-singh-web/taskmanager-backend/issues)

---

**Made with ❤️ by Vishal Singh**
