# Jarvis Android

On-device, persona-gebaseerde assistent (STT/TTS, lokale LLM, orb-UI).

## Download & installeren

1. Pak de nieuwste APK van de [**Releases**](https://github.com/stiflerstef-dev/jarvis-android/releases/latest)-pagina.
2. Open het `.apk`-bestand op je Android-telefoon.
3. Sta "installeren uit onbekende bronnen" toe als daarom gevraagd wordt.

> De builds zijn `arm64-v8a` (vrijwel elke moderne telefoon) en debug-signed.

## OTA self-update

De app controleert bij het starten `update.json` in deze repo. Zodra een nieuwe build
een hogere `versionCode` adverteert, biedt de app aan de update te downloaden en te
installeren — geen Play Store nodig.

`update.json`:

```json
{
  "versionCode": 2,
  "versionName": "0.2.0",
  "apkUrl": "https://github.com/stiflerstef-dev/jarvis-android/releases/download/v0.2.0/jarvis-0.2.0-arm64.apk",
  "notes": "Wat is er nieuw"
}
```

### Nieuwe versie uitbrengen

1. Bump `versionCode`/`versionName` in `android/app/build.gradle.kts`.
2. Bouw: `./gradlew assembleDebug -Pjarvis.abiFilters=arm64-v8a -Pjarvis.updateManifestUrl=https://raw.githubusercontent.com/stiflerstef-dev/jarvis-android/main/update.json`
3. Maak een release met de APK als asset.
4. Werk `update.json` bij (hogere `versionCode` + nieuwe `apkUrl`) en push naar `main`.
