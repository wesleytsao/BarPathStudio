# Privacy Policy for BarPath Studio

**Effective Date:** November 1, 2026  
**Last Updated:** November 1, 2026  
**Developer:** NeuralPrismLabs  
**Application:** BarPath Studio (iOS)

---

## 1. Overview & Zero-Cloud Architecture

**BarPath Studio** ("the App"), developed by **NeuralPrismLabs**, is an offline-first, 100% on-device Velocity-Based Training (VBT) and barbell trajectory analyzer designed for strength athletes and coaches.

We believe your biometric movement data, gym environment, and training logs belong exclusively to you. **BarPath Studio operates on a strict Zero-Cloud Architecture:**
- We do **not** operate external backend servers that collect, store, or process your personal data or workout videos.
- We do **not** require you to create an account, sign in, or provide an email address, name, or phone number to use the App.
- All computer vision object tracking and biomechanical kinematics calculations occur locally on your iPhone.

---

## 2. Camera & Computer Vision Data (`AVFoundation` & `Vision`)

BarPath Studio requests access to your device's camera (`NSCameraUsageDescription`) solely to track barbell plate displacement and compute lifting velocity in real time.

- **Volatile RAM Processing Only:** Live 60fps and 120fps camera frames (`CVPixelBuffer`) captured via Apple's `AVFoundation` framework are passed directly in volatile memory (RAM) to Apple's on-device `Vision` framework (`VNTrackObjectRequest`) and processed on the Apple Neural Engine (ANE) / GPU.
- **No Video or Image Recording:** Camera frames are immediately discarded from memory as soon as each frame's normalized $(x, y)$ barbell plate coordinate is extracted. The App does **not** record, save, or export raw video files or photographs to disk or any external server.
- **No Biometric or Facial Recognition:** The App tracks the geometric bounding box of a calibrated $0.45\text{m}$ ($450\text{mm}$) barbell plate end-cap. It never performs facial recognition, body pose identification, or biometric profiling.

---

## 3. Local Workout Storage (`SwiftData`)

When you choose to save a completed training set, BarPath Studio stores the following data locally on your device using Apple's **SwiftData** persistence framework:
- Exercise name (e.g., Back Squat, Bench Press, Deadlift, Snatch) and barbell load ($\text{kg}$).
- Repetition metrics: Mean Concentric Velocity ($\text{MCV}$), Peak Concentric Velocity, Velocity Loss Percentage ($\text{VL\%}$), and Range of Motion ($\text{ROM}$ in meters).
- A downsampled 60-point normalized $(x, y)$ coordinate array representing your best repetition's trajectory for the **PR Ghost Path Overlay** feature.

**Your Control Over Local Data:**
- All saved workout sessions reside strictly within the App's local iOS sandbox container on your device.
- You can delete individual workout sessions at any time inside the **VBT Workout Log (History)** view using the trash/delete action, or erase all local data permanently by uninstalling the App from your device.

---

## 4. Subscriptions & Payments (`StoreKit 2`)

BarPath Studio offers optional auto-renewable **BarPath Studio PRO** subscriptions (`$2.99/month` and `$19.99/year`) to unlock unlimited workout history and PR Ghost Path overlays.

- **Processed Exclusively by Apple:** All purchase transactions, subscription renewals, and entitlement verifications are handled directly by Apple Inc. through the native **StoreKit 2** framework and your Apple Account.
- **Zero Access to Payment Details:** NeuralPrismLabs never receives, processes, or stores your credit card number, billing address, Apple ID, or financial information. Cryptographic transaction verification is performed locally on-device using StoreKit 2's JWS (`Transaction.currentEntitlements`).

---

## 5. Third-Party Tracking, Analytics & Data Sharing

- **Zero Third-Party SDKs:** BarPath Studio contains **no** third-party advertising SDKs, **no** third-party analytics trackers (such as Firebase, Mixpanel, or Meta SDK), and **no** crash-reporting frameworks that transmit user identifiers.
- **Zero Cross-App Tracking (`IDFA`):** The App does not access the iOS Advertising Identifier (`IDFA`) and does not track you across other companies' apps or websites (`NSPrivacyTracking = false`).
- **No Sale or Sharing of Data:** Because we do not collect or transmit any personal data off your device, we never sell, rent, or share user data with any third party.

---

## 6. Children's Privacy

Because BarPath Studio does not collect, store, or transmit any personal information from any user of any age, the App complies with the Children's Online Privacy Protection Act (COPPA), the General Data Protection Regulation (GDPR), and the California Consumer Privacy Act (CCPA).

---

## 7. Contact Information

If you have any questions or feedback regarding this Privacy Policy, please contact us via our GitHub project page.
