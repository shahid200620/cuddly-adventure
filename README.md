# 🔐 PKI-Based 2FA Authentication Microservice

A secure, containerized authentication microservice implementing **Public Key Infrastructure (PKI)** and **Time-based One-Time Password (TOTP)** based **Two-Factor Authentication (2FA)**.  
Built as part of the **PATNR GPP Program** to demonstrate enterprise-grade backend security, cryptography, and DevOps practices.

---

## 📌 Project Overview

This project implements a production-style authentication microservice that:

- Uses **RSA 4096-bit encryption** for secure seed transmission
- Implements **TOTP-based 2FA** (Google Authenticator compatible)
- Runs as a **Dockerized microservice**
- Persists sensitive data using **Docker volumes**
- Logs 2FA codes automatically using **Linux cron**
- Demonstrates **cryptographic correctness & commit proof verification**

---

## 🧠 Key Concepts Demonstrated

- Public Key Infrastructure (PKI)
- RSA-OAEP Decryption (SHA-256)
- RSA-PSS Digital Signatures
- TOTP (RFC 6238)
- Secure key & seed handling
- REST API design
- Docker & Docker Compose
- Cron-based automation
- Persistent storage in containers

---

## ⚙️ Tech Stack

- **Language:** Python 3
- **Framework:** FastAPI
- **Crypto Library:** cryptography
- **2FA:** TOTP (SHA-1, 30s window, 6 digits)
- **Containerization:** Docker, Docker Compose
- **Automation:** Linux cron
- **Version Control:** Git & GitHub

---

## 🔑 Cryptography Details

| Feature | Specification |
|------|--------------|
| RSA Key Size | 4096 bits |
| Public Exponent | 65537 |
| Seed Encryption | RSA-OAEP (SHA-256 + MGF1) |
| Commit Signing | RSA-PSS (SHA-256, max salt length) |
| TOTP Algorithm | SHA-1 |
| TOTP Period | 30 seconds |
| TOTP Digits | 6 |

---

## 🌐 API Endpoints

### 🔓 `POST /decrypt-seed`
Decrypts the encrypted seed using the student private key and stores it persistently.

**Request**
```json
{
  "encrypted_seed": "BASE64_STRING"
}
