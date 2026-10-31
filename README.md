# VGRAM Private for Android

A self-hosted Android messenger client based on the OwpenGram / Telegram for Android codebase.

- Android minimum version: 5.0+ (the target test device is Android 12).
- MTProto API layer: 229.
- Build flavor: `:TMessagesProj_AppStandalone:assembleAfatDebug`.
- Application ID: `com.vgram.privateapp`.
- Display name: **VGRAM Private**.

## Current integration state

- The public upstream OwpenGram server has been removed from the built-in server list.
- The VGRAM Private built-in host is intentionally a reserved placeholder (`vgram-private.invalid`) until the VGRAM server is deployed.
- Use **Add server** with the real VGRAM server `host:port` after deployment. The client reads the server's RSA key and identity from its `/owpengram/server-info` endpoint.
- Login copy is adapted for codes delivered by the VGRAM Telegram bot.
- Upstream cloud strings, upstream auto-updates, Google/Huawei identity hooks, passkeys and Telegram billing are disabled in this build branch.

## Build

GitHub Actions builds a debug APK on pushes to `vgram-private` and stores it as the artifact **VGRAM-Private-Android-debug**.

For a local build with JDK 17 and Android SDK/NDK installed:

```sh
./gradlew --no-daemon :TMessagesProj_AppStandalone:assembleAfatDebug
```

A debug APK is for testing. A production release needs a VGRAM-owned signing key stored as GitHub Actions secrets; never commit keystore passwords or private signing keys.

## Server

- [VGRAM Private Server](https://github.com/ramzilzokirov-lgtm/owpengram-server)
- [VGRAM Private Server integration notes](https://github.com/ramzilzokirov-lgtm/owpengram-server/blob/vgram-private/docs/VGRAM_PRIVATE_INTEGRATION.md)

## License

This client is derived from Telegram for Android and OwpenGram. The applicable upstream license is GNU GPL v2 or later; see [LICENSE](LICENSE) and the source file headers.
