# Tejas Niranjan — 14th Birthday Website

A polished Cloudflare Pages-ready birthday invitation with:
- animated responsive landing page
- 9 October 2026 countdown
- venue map at the supplied coordinates
- one-tap Google Maps directions
- explicit, browser-permission-based guest location sharing
- Firebase Realtime Database RSVP/location backend hooks
- protected Firebase email/password admin dashboard
- real-time guest markers for authorized admins

## Important privacy design
Guest location is **opt-in**. The browser asks for permission only after the guest taps **Share my location**. Admin access is intended for authorized accounts only. Do not publish an admin password or Firebase service-account credentials in frontend code.

## Firebase setup
1. Create a Firebase project.
2. Enable Authentication → Email/Password and Anonymous authentication.
3. Create a Realtime Database.
4. Add a Web App and copy its config into both `index.html` and `admin.html`.
5. Create the admin email/password account in Firebase Authentication.
6. In Realtime Database, set `/admins/<ADMIN_UID>` to `true`.
7. Replace database rules with `firebase-rules.json`.
8. Deploy `index.html` and `admin.html` to Cloudflare Pages.

## Venue
25.455835022731513, 78.63566455483142

## Recommended production hardening
- Keep a short retention period for location records.
- Store only the latest location rather than a detailed travel history unless there is a specific need and clear consent.
- Add a visible “Stop sharing” control (already present).
- Use HTTPS (Cloudflare Pages provides this).
- Consider a separate server-side audit log for admin access.
