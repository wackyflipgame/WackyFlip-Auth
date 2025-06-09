# 🔐 WackyFlip-Auth

Authentication & User Management Service
A secure, scalable system managing user accounts, session tokens, login workflows, and social/OAuth authentication for the [Wacky Flip](https://wackyflip.com) ecosystem.

---

## 📋 Overview

`WackyFlip-Auth` is the backbone of user identity and access control across all Wacky Flip platforms. It handles everything from account creation and password management to secure session handling and third-party OAuth integrations (Google, Facebook, etc.).

Designed with security best practices, it provides token-based authentication, password hashing, multi-factor auth extensibility, and smooth user experiences across web and mobile.

---

## ⚙️ Key Features

* 🔑 **User Account Management**
  Register, update, and delete user accounts with email verification and password recovery.

* 🛡️ **Secure Authentication**
  Implements JWT-based authentication with refresh tokens and secure cookie handling.

* 🌐 **OAuth & Social Login**
  Support for Google, Facebook, and other OAuth providers for quick sign-in.

* 🔒 **Session & Token Management**
  Issue, verify, and revoke access and refresh tokens to manage user sessions securely.

* 📧 **Email Notifications**
  Send verification, password reset, and security alert emails.

* 🧩 **Role-Based Access Control (RBAC)**
  Define and enforce user roles and permissions for different parts of the platform.

* 🔍 **Audit Logging**
  Record authentication events, login attempts, and suspicious activity for security monitoring.

---

## 🧱 Tech Stack

* **Node.js + Express** – API server framework
* **MongoDB** – User data and token storage
* **Redis** – Token blacklist and session caching
* **Passport.js** – OAuth strategy integrations
* **bcrypt** – Password hashing
* **JWT** – JSON Web Tokens for authentication
* **Nodemailer** – Email delivery for notifications and verifications

---

## 📁 Directory Structure

```
WackyFlip-Auth/
├── src/
│   ├── controllers/      # Account, auth, and OAuth logic
│   ├── routes/           # Express routes for login, register, token refresh
│   ├── models/           # User, token, and session schemas
│   ├── middleware/       # Auth validation, role checks, rate limiting
│   ├── services/         # OAuth strategies, email service, token management
│   └── utils/            # Helpers (hashing, validation)
├── config/
│   └── db.js             # DB connections
├── tests/                # Unit and integration tests
├── .env                  # Environment variables
├── app.js                # Entry point
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/wackyflipgame/WackyFlip-Auth.git
cd WackyFlip-Auth
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment

Create a `.env` file based on `.env.example` and configure:

* Database URIs
* JWT secrets
* OAuth client IDs & secrets
* SMTP server details for emails

### 4. Run the Server

```bash
npm start
```

The service will start on `http://localhost:4000`

---

## 🔄 Authentication Workflow

1. **Registration:** New users sign up with email & password. Verification email sent.
2. **Login:** Users authenticate with email/password or via OAuth providers.
3. **Token Issuance:** JWT access and refresh tokens are issued on successful login.
4. **Session Management:** Tokens validated on every request; refresh tokens allow session continuation.
5. **Logout:** Tokens revoked and blacklisted.
6. **Password Reset:** Email-based reset workflow.

---

## 📚 API Endpoints

| Method | Endpoint                       | Description                                   | Auth Required |
| ------ | ------------------------------ | --------------------------------------------- | ------------- |
| POST   | `/auth/register`               | Register new user                             | No            |
| POST   | `/auth/login`                  | User login with email & password              | No            |
| POST   | `/auth/oauth/:provider`        | OAuth login callback (Google, Facebook, etc.) | No            |
| POST   | `/auth/token`                  | Refresh access token                          | Yes           |
| POST   | `/auth/logout`                 | Invalidate tokens and logout                  | Yes           |
| POST   | `/auth/password-reset/request` | Request password reset email                  | No            |
| POST   | `/auth/password-reset/confirm` | Confirm new password                          | No            |
| GET    | `/users/me`                    | Get current user profile                      | Yes           |

---

## 🧪 Testing

```bash
npm run test
```

Tests cover authentication flows, OAuth integration, and token validation.

---

## 🔐 Security

* Passwords hashed using bcrypt with salt
* HTTPS recommended in production
* Rate limiting to prevent brute force attacks
* Token blacklisting for immediate revocation
* OAuth tokens handled securely with Passport.js strategies

---

## 🤝 Contributing

Contributions to enhance authentication security, support new OAuth providers, or improve user management are welcome!

Fork → Branch → Pull Request.

---

## 📜 License

MIT License © Wacky Flip Studios

---

## 🔗 Related Repositories

* [`WackyFlip-API`](https://github.com/wackyflipgame/WackyFlip-API) – API gateway consuming this auth service
* [`WackyFlip-Web`](https://github.com/wackyflipgame/WackyFlip-Web) – Frontend integrating login & user sessions
* [`WackyFlip-Stats`](https://github.com/wackyflipgame/WackyFlip-Stats) – User stats linked with authenticated users
