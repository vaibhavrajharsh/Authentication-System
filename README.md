# 🔐 Authentication System using Express.js, JWT, and Cookie Parser

A secure authentication system built with **Node.js**, **Express.js**, **JSON Web Tokens (JWT)**, and **Cookie Parser**. This project provides user registration, login, protected routes, and logout functionality using JWT stored in HTTP cookies.

---

## 🚀 Features

- User Registration
- User Login
- JWT-Based Authentication
- Secure Cookie Storage
- Protected Routes
- User Logout
- Password Hashing with bcrypt
- Middleware for Token Verification

---

## 🛠️ Technologies Used

- Node.js
- Express.js
- MongoDB
- Mongoose
- JSON Web Token (JWT)
- Cookie Parser
- bcryptjs
- dotenv

---

## 📦 Installation

### Clone the Repository

```bash
git clone https://github.com/yourusername/authentication-system.git
cd authentication-system

Install Dependencies

npm install

Required Packages

npm install express mongoose jsonwebtoken cookie-parser bcryptjs dotenv

---

📁 Project Structure

authentication-system/
│
├── controllers/
│   └── authController.js
│
├── middleware/
│   └── authMiddleware.js
│
├── models/
│   └── User.js
│
├── routes/
│   └── authRoutes.js
│
├── .env
├── server.js
└── package.json

---

⚙️ Environment Variables

Create a ".env" file and add:

PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key

---

📌 API Endpoints

Register User

POST "/api/auth/register"

Request Body

{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}

Response

{
  "message": "User registered successfully"
}

---

Login User

POST "/api/auth/login"

Request Body

{
  "email": "john@example.com",
  "password": "password123"
}

Response

{
  "message": "Login successful"
}

A JWT token is generated and stored in an HTTP cookie.

---

Get User Profile

GET "/api/auth/profile"

Response

{
  "message": "Access granted"
}

Only authenticated users can access this route.

---

Logout User

POST "/api/auth/logout"

Response

{
  "message": "Logged out successfully"
}

The authentication cookie is cleared during logout.

---

🔄 Authentication Flow

1. User registers an account.
2. User logs in using email and password.
3. Server validates the credentials.
4. JWT token is generated.
5. Token is stored inside a cookie.
6. Middleware verifies the token before accessing protected routes.
7. User logs out and the cookie is removed.

---

🔒 Example Middleware

const jwt = require("jsonwebtoken");

const verifyToken = (req, res, next) => {
    const token = req.cookies.token;

    if (!token) {
        return res.status(401).json({
            message: "Unauthorized"
        });
    }

    try {
        const decoded = jwt.verify(token, process.env.JWT_SECRET);

        req.user = decoded;

        next();
    } catch (error) {
        res.status(401).json({
            message: "Invalid token"
        });
    }
};

module.exports = verifyToken;

---

🔐 Security Features

- Passwords are hashed using bcrypt.
- JWT tokens are signed using a secret key.
- Tokens are stored securely in cookies.
- Middleware protects private routes.
- Environment variables are used for sensitive information.

---

📈 Future Improvements

- Refresh Tokens
- Email Verification
- Forgot Password Functionality
- Role-Based Authorization
- OAuth Authentication (Google/GitHub)
- Rate Limiting and Security Headers

---

🤝 Contributing

Contributions are welcome. Feel free to fork the repository and submit pull requests.

---

📜 License

This project is licensed under the MIT License.

---

👨‍💻 Author

Developed with ❤️ using Express.js, JWT, and Cookie Parser.
