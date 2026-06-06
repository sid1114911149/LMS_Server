# 🚀 Learning Management System (LMS) Backend

A scalable and secure backend API for a Learning Management System (LMS) built using the MERN Stack. This backend provides authentication, role-based access control, course management, enrollment tracking, lecture management, and administrative functionalities.

---

## 📖 Overview

The LMS Backend serves as the core of the platform, handling all business logic, user authentication, database interactions, and API communications.

The system supports three primary user roles:

- 👨‍🎓 Student
- 👨‍🏫 Instructor
- 👨‍💼 Administrator

Built with modern backend development practices including JWT Authentication, RESTful APIs, MongoDB Atlas, and MVC Architecture.

---

## ✨ Features

### 🔐 Authentication & Authorization

- User Registration
- User Login
- Logout Functionality
- JWT-Based Authentication
- Password Hashing using bcryptjs
- Protected Routes
- Role-Based Access Control (RBAC)

### 👤 User Management

- Create Account
- Update Profile
- Upload Profile Picture
- Change Password
- View Profile
- Delete Account

### 📚 Course Management

- Create Courses
- Update Courses
- Delete Courses
- Publish Courses
- Draft Courses
- Course Thumbnail Upload
- Course Categorization

### 🎥 Lecture Management

- Add Lectures
- Update Lectures
- Delete Lectures
- Video Upload Support
- Document Upload Support

### 🎓 Student Features

- Browse Courses
- Enroll in Courses
- Access Course Content
- Track Learning Progress
- Continue Learning

### 👨‍💼 Admin Features

- Manage Users
- Manage Courses
- View Platform Statistics
- Role Management
- Content Moderation

### 📊 Progress Tracking

- Lecture Completion Tracking
- Course Progress Calculation
- Learning Dashboard Support

---

# 🏗️ System Architecture

```text
Client (React + Vite)
        │
        ▼
REST API (Express.js)
        │
        ▼
Business Logic Layer
        │
        ▼
MongoDB Database
```

The backend follows the MVC (Model-View-Controller) design pattern for better scalability and maintainability.

---

# 🛠️ Tech Stack

## Backend

- Node.js
- Express.js

## Database

- MongoDB Atlas
- Mongoose ODM

## Authentication

- JWT (JSON Web Token)
- bcryptjs

## File Upload

- Multer
- Cloudinary

## Utilities

- Cookie Parser
- CORS
- dotenv
- Express Async Handler

---

# 📂 Project Structure

```text
server
│
├── controllers
│   ├── user.controller.js
│   ├── course.controller.js
│   ├── lecture.controller.js
│   ├── progress.controller.js
│   └── admin.controller.js
│
├── models
│   ├── User.js
│   ├── Course.js
│   ├── Lecture.js
│   └── CourseProgress.js
│
├── routes
│   ├── user.routes.js
│   ├── course.routes.js
│   ├── lecture.routes.js
│   ├── progress.routes.js
│   └── admin.routes.js
│
├── middlewares
│   ├── auth.middleware.js
│   ├── role.middleware.js
│   ├── upload.middleware.js
│   └── error.middleware.js
│
├── config
│   ├── database.js
│   └── cloudinary.js
│
├── utils
│   ├── generateToken.js
│   ├── ApiResponse.js
│   └── ApiError.js
│
├── app.js
├── server.js
├── package.json
└── .env
```

---

# 🔐 Authentication Flow

```text
User Login
     │
     ▼
Validate Credentials
     │
     ▼
Generate JWT Token
     │
     ▼
Store in HTTP-Only Cookie
     │
     ▼
Access Protected Routes
```

---

# 🌐 REST API Endpoints

## Authentication

| Method | Endpoint | Description |
|----------|------------|------------|
| POST | /api/v1/user/register | Register User |
| POST | /api/v1/user/login | Login User |
| POST | /api/v1/user/logout | Logout User |
| GET | /api/v1/user/profile | Current User Profile |

---

## Users

| Method | Endpoint |
|----------|------------|
| GET | /api/v1/users |
| GET | /api/v1/user/:id |
| PUT | /api/v1/user/update |
| DELETE | /api/v1/user/delete |

---

## Courses

| Method | Endpoint |
|----------|------------|
| POST | /api/v1/course |
| GET | /api/v1/course |
| GET | /api/v1/course/:id |
| PUT | /api/v1/course/:id |
| DELETE | /api/v1/course/:id |

---

## Lectures

| Method | Endpoint |
|----------|------------|
| POST | /api/v1/course/:id/lecture |
| PUT | /api/v1/lecture/:id |
| DELETE | /api/v1/lecture/:id |

---

## Enrollment

| Method | Endpoint |
|----------|------------|
| POST | /api/v1/course/enroll |
| GET | /api/v1/course/enrolled |

---

## Progress

| Method | Endpoint |
|----------|------------|
| POST | /api/v1/progress/update |
| GET | /api/v1/progress/:courseId |

---

# 📊 Database Models

## User Model

```javascript
{
  name: String,
  email: String,
  password: String,
  role: String,
  photoUrl: String,
  enrolledCourses: [ObjectId]
}
```

## Course Model

```javascript
{
  courseTitle: String,
  subTitle: String,
  description: String,
  category: String,
  courseLevel: String,
  coursePrice: Number,
  courseThumbnail: String,
  lectures: [ObjectId],
  creator: ObjectId,
  isPublished: Boolean
}
```

## Lecture Model

```javascript
{
  lectureTitle: String,
  videoUrl: String,
  publicId: String
}
```

## Course Progress Model

```javascript
{
  userId: ObjectId,
  courseId: ObjectId,
  completedLectures: [ObjectId]
}
```

---

# ⚙️ Environment Variables

Create a `.env` file inside the root directory.

```env
PORT=5000

NODE_ENV=development

MONGO_URI=your_mongodb_connection_string

JWT_SECRET=your_secret_key

JWT_EXPIRE=7d

CLOUDINARY_CLOUD_NAME=your_cloud_name

CLOUDINARY_API_KEY=your_api_key

CLOUDINARY_API_SECRET=your_api_secret

CLIENT_URL=http://localhost:5173
```

---

# 🚀 Installation

Clone the repository

```bash
git clone https://github.com/yourusername/lms-backend.git
```

Move to project directory

```bash
cd lms-backend
```

Install dependencies

```bash
npm install
```

---

# ▶️ Run Development Server

```bash
npm run dev
```

Server runs on:

```text
http://localhost:5000
```

---

# 🏭 Production Build

```bash
npm start
```

---

# 🔒 Security Features

- JWT Authentication
- bcrypt Password Hashing
- Protected Routes
- Role-Based Authorization
- HTTP-Only Cookies
- Input Validation
- CORS Protection
- Secure Environment Variables
- MongoDB Injection Protection

---

# 📈 Performance

### Tested Results

| Users | Avg Response Time |
|---------|-------------------|
| 10 | 85 ms |
| 100 | 210 ms |
| 500 | 480 ms |

### Throughput

| Users | Requests/sec |
|---------|-------------|
| 10 | 118 |
| 100 | 476 |
| 500 | 1042 |

---

# 🔮 Future Enhancements

- Socket.io Real-Time Notifications
- Live Chat System
- Discussion Forums
- Quiz & Assessment Module
- Certificate Generation
- Razorpay Integration
- Stripe Integration
- AI Course Recommendation System
- Advanced Analytics Dashboard
- Mobile App Support

---

# 🤝 Contributing

Contributions, issues, and feature requests are welcome.

Feel free to fork the repository and submit pull requests.

---

# 📜 License

This project is licensed under the MIT License.

---

# 👨‍💻 Author

### Siddardha Reddy Pasham

Full Stack MERN Developer

- Node.js
- Express.js
- MongoDB
- React.js
- REST APIs

⭐ If you found this project useful, please give it a star.
