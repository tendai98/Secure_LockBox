# Secure Lock Box 🗝️📦

The project comprises two modules: **Secure_Lock_Box** and **Secure_Lock_Box_WNIC**. It uses biometric authentication and GPS tracking to secure a lock box.

## Project Overview 📝

### Secure_Lock_Box Module
This module deals with fingerprint enrollment, authentication, and lock control.

- **Code Files:**
  - `const.h`, `fps.h`, `gps.h`, `Secure_Lock_Box.ino`, `servo.h`
- **Functionalities:**
  - `const.h`: Defines various operation codes for lock control and authentication.
  - `fps.h`: Handles fingerprint sensor-related functions such as enrollment, authentication, and image processing.
  - `gps.h`: Manages GPS-related operations for obtaining location data.
  - `Secure_Lock_Box.ino`: Contains the main setup and loop logic for integrating the functionalities.
  - `servo.h`: Controls the servo motor for locking and unlocking the box.

### Secure_Lock_Box_WNIC Module
This module interacts with the network for OTP authentication and GPS data transmission.

- **Code Files:**
  - `const.h`, `net.h`, `server.h`, `server_routes.h`
- **Functionalities:**
  - `const.h`: Holds constant values for different operation codes, HTTP responses, and default MIME types.
  - `net.h`: Manages Wi-Fi connectivity and communication.
  - `server.h`: Initializes an HTTP server and defines various server routes.
  - `server_routes.h`: Implements functions for different server routes such as unlocking, locking, OTP authentication, GPS data retrieval, etc.

## How It Works ℹ️

1. **Fingerprint Enrollment:** Capture and store fingerprints for user authentication.
   - `enrollFingerprints()` in `Secure_Lock_Box.ino` initiates fingerprint enrollment.
2. **Biometric Authentication:** Scan fingerprints and grant access based on recognition.
   - `scanFingerprint()` in `Secure_Lock_Box.ino` authenticates users based on stored fingerprints.
3. **Lock/Unlock Control:** Manage the servo motor to lock or unlock the box.
   - `runLockProc()` and `runUnLockProc()` in `servo.h` control the servo motor to lock and unlock the box.
4. **Wi-Fi Interaction:** Handle network communication for OTP verification and GPS data transmission.
   - HTTP server routes in `server_routes.h` handle various functionalities such as unlocking, locking, OTP authentication, GPS data transmission, etc.

## Code 🧩

- **`runProc()`:** Enrolls fingerprints and stores them for authentication.
- **`scanFingerprint()`:** Scans a fingerprint for authentication.
- **`shutdownGPS()`:** Shuts down the GPS module.
- **`sendGPSData()`:** Sends GPS data to the connected device.
- **`executeOpcode(char opcode)`:** Executes operations based on received opcodes.
- **Server routes' functions** like `unlockBox()`, `lockBox()`, `biometricAuth()`, `enrollBiometric()`, `pinCodeAuth()`, `setOTPAuthCode()`, `resetDevice()`, `sendBoxId()`, and `getGPSData()` handle specific HTTP requests for respective actions.

## Usage 🚀

- **Secure_Lock_Box Module:**
  - Ensure proper wiring of the fingerprint sensor and servo motor.
  - Upload the code to the microcontroller.
- **Secure_Lock_Box_WNIC Module:**
  - Configure Wi-Fi credentials in `net.h`.
  - Upload the code to the microcontroller.
  - Use appropriate HTTP requests to interact with the lock box functionalities.

## Additional Notes ℹ️

- Customize the pin configurations and sensor settings as per your hardware connections.
- Ensure the availability of sufficient power for stable functioning.
- OTP authentication adds an additional layer of security for accessing the lock box.
