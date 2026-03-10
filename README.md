# Cryptography

## Project Overview
This project demonstrates fundamental cryptography concepts, including **symmetric encryption** (Fernet/AES) and **asymmetric encryption** (RSA).  
The goal is to encrypt and decrypt messages to understand data security principles.

---

## Tools and Environment
- **Operating System:** Linux / WSL
- **Programming Language:** Python 3.13
- **Python Libraries:** cryptography
- **Commands Used:**
  - `python3` → run Python scripts
  - `pip install cryptography` → install required library

---
## Symmetric Encryption (Fernet / AES)

### Code Snippet:
```python
from cryptography.fernet import Fernet

# Generate key
key = Fernet.generate_key()
cipher = Fernet(key)

# Encrypt message
message = b"My secret message"
encrypted = cipher.encrypt(message)
print("Encrypted:", encrypted)

# Decrypt message
decrypted = cipher.decrypt(encrypted)
print("Decrypted:", decrypted.decode())

Sample Output:
Encrypted: b'gAAAAABk...'
Decrypted: My secret message;

##<img width="2735" height="1719" alt="Screenshot 2026-03-10 224426" src="https://github.com/user-attachments/assets/426fe73c-4ab9-4328-9d51-05ce0f04c714" />

##Asymmetric Encryption (RSA)
#Code Snippet:

from cryptography.hazmat.primitives import serialization, hashes
from cryptography.hazmat.primitives.asymmetric import rsa, padding

# Generate RSA keys
private_key = rsa.generate_private_key(public_exponent=65537, key_size=2048)
public_key = private_key.public_key()

# Encrypt message
message = b"Secret message"
encrypted = public_key.encrypt(
    message,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)
print("Encrypted:", encrypted)

# Decrypt message
decrypted = private_key.decrypt(
    encrypted,
    padding.OAEP(
        mgf=padding.MGF1(algorithm=hashes.SHA256()),
        algorithm=hashes.SHA256(),
        label=None
    )
)
print("Decrypted:", decrypted.decode())
##Sample Output:
Encrypted: b'\x12\xab...'
Decrypted: Secret message;

##<img width="2704" height="1723" alt="Screenshot 2026-03-10 231508" src="https://github.com/user-attachments/assets/7562dc8f-c233-41f0-9ebb-336a6170ec23" />

##Steps Followed

Verified Python installation: python3 --version

Installed cryptography library: pip install cryptography

Created Python scripts for symmetric and asymmetric encryption

Tested scripts with sample messages

Captured outputs and screenshots for documentation

##Conclusion

Symmetric Encryption: Fast, uses a single key (Fernet/AES)

Asymmetric Encryption: Uses public/private key pair (RSA), solves key distribution problem

Python cryptography library provides an easy interface for cryptography operations

Hands-on practice helps understand encryption, decryption, and key management
