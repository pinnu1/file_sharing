# 📁 Secure File Sharing System

This repository contains a **secure file-sharing REST API** built using **FastAPI**. It supports **role-based access control**, **JWT authentication**, and secure **one-time download links**, ensuring safe delivery of files between operation users and clients.

---

## 🛠 Tech Stack

- **Language**: Python 3  
- **Framework**: FastAPI  
- **Authentication**: JWT (OAuth2), Role-based (Ops, Client)  
- **Encryption**: Fernet (used for secure email verification tokens)  
- **Data Storage**: In-memory (Python dictionaries for simplicity)  
- **API Testing**: Postman (collection included)  
- **Package Management**: pip (`requirements.txt`)  

---

## 📁 Project Structure

```
secure_file_sharing/
├── main.py                              # Main application file
├── .env                                 # Environment configuration
├── requirements.txt                     # Python dependencies
├── SecureFileSharingAPI.postman_collection.json  # Postman collection
└── README.md                            # Project documentation
```

---

## ✅ Features

- 🔐 User registration with role selection (`client`, `ops`)
- 📧 Email verification using a secure Fernet token
- 🔑 JWT-based login and token-based authorization
- 📤 Upload capability for operations team only
- 📂 File listing and downloading for verified clients
- 🔗 Secure one-time download links for files
- 📊 Simulated download tracking per client

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/pinnu1/secure_file_sharing.git
cd secure_file_sharing
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Set Up Environment Variables

Create a `.env` file in the project root with the following keys:

```env
SECRET_KEY=your_jwt_secret_key
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
FERNET_KEY=your_fernet_key_here
```

Generate a Fernet key using:

```python
from cryptography.fernet import Fernet
print(Fernet.generate_key().decode())
```

### 4. Run the Application

```bash
uvicorn main:app --reload
```

Access the API at:  
📎 [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)

---

## 📡 API Endpoints

| Method | Endpoint                         | Access Role | Description                          |
|--------|----------------------------------|-------------|--------------------------------------|
| POST   | `/signup`                        | Public      | Register a new user                  |
| GET    | `/verify-email/{token}`          | Public      | Verify user's email                  |
| POST   | `/login`                         | Public      | User login and receive JWT token     |
| POST   | `/upload`                        | Ops only    | Upload files                         |
| GET    | `/list-files`                    | Client only | View list of uploaded files          |
| GET    | `/download-file/{file_id}`       | Client only | Generate a secure file download link |
| GET    | `/secure-download/{token}`       | Client only | One-time download using token        |
| GET    | `/download-history`              | Client only | View download history (simulated)    |

---

## 🧪 API Testing with Postman

1. Open Postman and import the collection:  
   `SecureFileSharingAPI.postman_collection.json`

2. Test the API by following this flow:

   - ➕ **Sign Up** using `/signup`
   - 📧 **Verify Email** using `/verify-email/{token}`
   - 🔐 **Login** via `/login` and capture the `access_token`
   - 📤 **Upload Files** as an `ops` user
   - 📥 **List & Download Files** as a `client` user

---

## 📬 Contact

Created and maintained by **Prashant Garg**  
📧 Email: aprashant703@gmail.com  
💼 GitHub: [https://github.com/pinnu1](https://github.com/pinnu1)

---
