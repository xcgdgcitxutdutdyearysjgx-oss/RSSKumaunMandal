# RSSKumaunMandal Android project

Application ID: `com.priyanshu.pk`
Target/Compile SDK: 36
minSdk: 23
Billing: 8.0.0
Version: 23.0.0 / versionCode 230000

## Firebase setup
1. Create a Firebase project and an Android/Web app configuration.
2. Copy `app/src/main/assets/firebase-config.js.example` to `firebase-config.js` and fill the Web App config.
3. Enable Realtime Database, Storage and Authentication.
4. For production admin security, create the admin in Firebase Authentication and enforce Storage/Database Rules. The visible sample login is only a bootstrap UI and is NOT a secure server-side credential check.
5. For uploads, Storage rules should permit only authenticated admin writes; public users should have read-only access to published content.

## Release signing
Generate/use a strong RSA 2048+ upload key. Do not commit the keystore or passwords. Configure signing in `app/build.gradle.kts` using environment variables or `keystore.properties` before release.

## Version code
`230000` is intentionally high. For an existing Play app, it MUST be greater than the currently published/uploaded versionCode. If your existing versionCode is already >= 230000, increase it again.

## Build
Open in Android Studio, let Gradle sync, add Firebase config, configure release signing, then Build > Generate Signed App Bundle. This environment does not contain the Android SDK/Gradle toolchain, so no verified AAB is claimed from this source package.

## Strong key
`generate_upload_key.ps1` creates an RSA-4096 PKCS12 upload key. Keep the `.jks`/`.p12` and passwords private. If Google Play App Signing is already enabled, this is an upload key; if Play expects your existing upload key, use the existing key or follow Play Console's upload-key reset process.
