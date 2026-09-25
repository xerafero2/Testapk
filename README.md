# Sandbox Manager

MVP Android project for staging APKs inside the application's private storage.

## Important security limitation

This version does **not** execute imported APKs. It is intentionally limited to:
- importing an APK into app-private storage;
- keeping APK data separate from normal shared storage;
- calculating SHA-256;
- listing/deleting staged APKs;
- building through GitHub Actions.

A normal Android application cannot simply create a fully isolated "Android inside Android" environment for arbitrary APKs. True execution isolation requires a virtualization/container backend with appropriate privileges and Android kernel/VM support.

## Build with GitHub Actions

1. Create a GitHub repository.
2. Upload this project.
3. Push to `main` or `master`.
4. Open **Actions → Build APK**.
5. Download the `SandboxManager-debug` artifact.

## Next backend

For a real isolated execution product, the next stage should be a VM/guest-Android backend. The UI can then treat each guest as an instance:

- Instance 1 → guest storage + guest package manager
- Instance 2 → separate guest storage + package manager
- Instance N → separate guest

Do not treat this MVP as a guarantee that a malicious APK is safe to execute.
