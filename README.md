# Xiaomi-privacy-bypass
Bypass Xiaomi’s Privacy Password without factory reset.

# Xiaomi Privacy Password Bypass (No Factory Reset)

# DISCLAIMER: Someone reported that they lost old files, but files from the last three months remained untouched. Use this method at YOUR OWN RISK.

This guide explains how to **disable Xiaomi's Privacy Password** without a factory reset. Tested and confirmed working on **Xiaomi Note 12** (HyperOS 2.0.9.0). 

## Disclaimer
This guide is for **educational purposes only**. Use it only on your own device. I'm not responsible for any issues that arise from following this method.

## Requirements
- You **must be able to unlock and access your phone** (this method will not work if the phone is completely locked).  
- The phone must be running MIUI with **Developer Options enabled**.
- Internet access required to install apps.  

## Prerequisites 1️⃣
1. Enable Developer Options:
   - Go to Settings > About Phone
   - Tap OS version 7 times until you see "You are now a developer!"
2. Enable USB Debugging:
   - Go to Settings > Additional Settings > Developer Options
   - Enable USB Debugging
   - Enable USB Debugging (Security Settings) -- This is different from Enable USB Debugging; you will know why later on (from Shizuku Guide).
3. Install Shizuku & SetEdit:
   - Download Shizuku: https://play.google.com/store/apps/details?id=moe.shizuku.privileged.api
   - Download SetEdit: https://play.google.com/store/apps/details?id=by4a.setedit22

## Step-by-Step Guide 2️⃣
1. Start Shizuku
   - Open Shizuku, follow the instructions, and start the service.
   - Change notification style from Classic to Android -- you will know why later on (from Shizuku Guide).
   - Here is their Guide: https://shizuku.rikka.app/guide/setup/#start-shizuku

2. Grant SetEdit Permissions
   - Open Shizuku, go to the "Apps" tab.
   - If you see SetEdit, tap it and grant shell permissions.
   - If SetEdit doesn't appear, you can ignore it or try manually granting permissions using ADB. If you proceed without it and it still doesn't work, consider using ADB.

3. Modify Privacy Password Settings
   - Open SetEdit.
   - Tap the dropdown in SetEdit, change 'System Table' to 'Secure Table' at the top right.
   - Locate these settings:
     - `privacy_password_is_open`
     - `access_control_lock_enabled`
   - Change their values to `0`.
   - If they don't exist, add them manually.
   - It auto-saves so just exit the app.

4. Reboot Your Phone
   - Restart your phone to apply the changes.
   - Check if Privacy Password is disabled.
   - You will be prompted to set a new one.

##  Optional Cleanup 3️⃣
- Turn off Developer Options (optional but recommended).
- Uninstall Shizuku & SetEdit to keep things clean.
- Change notification style back to Classic.


**You're all set!**

## ADB Guide (Optional, if SetEdit Doesn’t Appear and it didn't work) 4️⃣
If SetEdit doesn't appear in Shizuku and the method didn't work, you can try manually granting its permissions via ADB:
### Steps:
1. Install **ADB on your PC**:
   - Download platform tools: https://developer.android.com/studio/releases/platform-tools
   - Extract and open the folder.
2. Connect your phone to the PC via USB or follow this guide https://www.xda-developers.com/install-adb-windows-macos-linux/.
3. Open a command prompt in the platform-tools folder and enter:
   ```sh
   .\adb devices
   ```
   - If your device appears, proceed.
   - If it asks for permission on the phone, accept it.
4. Enter the following command to grant SetEdit permissions:
   ```sh
   .\adb shell pm grant by4a.setedit22 android.permission.WRITE_SECURE_SETTINGS
   ```
5. If successful, continue with the next steps 3 and 4 from Step-by-Step Guide 2️⃣. I personally did this step, but SetEdit still didn't appear in Shizuku. I continued anyway, and it still worked.

You have successfully disabled Xiaomi’s Privacy Password without losing data.
