# my_app

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://flutter.dev/docs/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://flutter.dev/docs/cookbook)

For help getting started with Flutter, view our
[online documentation](https://flutter.dev/docs), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

# Getting Started with Flutter Development with Android devices #  

*Note* I'm not interested in emulating the app on iOS devices right now. 

Following the ['Get Started'](https://flutter.dev/docs/get-started/install/macos) tutorial 
from Flutter got me ~60% of the way to writing my first app. Here are a few issues I ran 
into along the way, and the resources I used to fix them.  

## Using `flutter doctor` to Diagnose Problems ##  

Flutter will notify you that things are missing by simply running `flutter doctor -v` in terminal.
The `-v` is a verbose flag, meaning you'll get a more detailed messsage about what might be wrong
or missing. I recommend always adding this flag, since then the help messages will provide links to 
online resources you can check out for even more help. 

## Emualted Pixel Series not connected ##  

Emulated devices can be managed from Android Studio >> Configure >> AVD Manager and following
the on screen prompts.

I tried using different devices from the Pixel series, however I was unable to resolve connectivity 
issues. 

Switching to a Nexus 6 worked out of the box. The device is using the R system image and Android 11.0

I found this solution by reading [this StackOverflow comment](https://stackoverflow.com/a/60999459).

## Authorizing your device ##
Running the emulator and checking `flutter doctor -v` at this stage shows something like:

```
[!] Connected device
• Device emulator-5554 is not authorized. //-5554 may be different depending on your number of devices
  You might need to check your device for an authorization dialog.
```

To authorize the device, you need to be in developer mode and enable USB debugging. Following the steps
found on [this StackOverflow comment](https://stackoverflow.com/a/54974886) (from the same question as above)
was helpful.

*Note* You can check your available devices and emulators by typing `flutter devices` or `flutter emulators`.

## Android Studio plugins not recognized##  

Even if the Flutter and Dart plugins are properly installed on your Android Studio, `flutter doctor -v` may still
warn you that:

```
    ✗ Flutter plugin not installed; this adds Flutter specific functionality.
    ✗ Dart plugin not installed; this adds Dart specific functionality.
```

Flutter applications can be written on other IDEs, not just Android Studio. I prefer using VSCode and
according to `flutter doctor -v` VSCode plugins are ok:

```
[✓] VS Code (version 1.50.1)
```

According to [this GitHub Issue](https://github.com/flutter/flutter/issues/67986#issuecomment-707511812), Flutter
will still work fine without the plugins. 

## Android Studio is not detected ##  

Trying to fix the plugins issue, I caused this problem:

```
✗ Android Studio not found at /Users/name/Library/Android/sdk/Contents
```

The path to your Android Studio installation can be changed by running `flutter config --android-studio-dir=<path/to/install>`.
Trying `flutter config --android-studio-dir=/Users/name/Library/Android/sdk/Contents` from [this GitHub Issue](https://github.com/flutter/flutter/issues/67986#issuecomment-707508419) did not work for me. 

However, running `flutter config --android-studio-dir=` removed the config setting. 

This solution was found in the same issue thread as before. [Here's a link](https://github.com/flutter/flutter/issues/67986#issuecomment-707717572)









