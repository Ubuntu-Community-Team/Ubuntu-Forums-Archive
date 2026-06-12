---
title: "Dual monitors get harder with each successive release of Ubuntu"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2011-08-07
I have two monitors with the right-hand monitor rotated to portrait orientation, and have been successfully using this setup through several versions of Ubuntu. Having just purchased an SSD, I decided to install 11.04 on it (previously using 10.04). I can't get a desktop to appear after login - when the login screen appears, both monitors are at the correct resolution and orientation, and I can pan the mouse pointer across both monitors, and after logging in I have the correct desktop background and can still pan the mouse pointer across both monitors, but that's it - no desktop appears and right-click of the mouse doesn't show the popup menu I'd expect. I tried the Gnome desktop as well as Unity and the problem happens with both. All I can do at that point is Ctrl+Alt+F1 to to get to a text screen so I can login, copy back the xorg.conf for the single monitor only, and reboot back to a single monitor setup.

This is the xorg.conf for the dual monitor setup. From the mouse behaviour it seems that the X configuration is correct for the monitor layout I have:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" 2560 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Dell 3008WFP"
    HorizSync       29.0 - 113.0
    VertRefresh     49.0 - 86.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "DELL U2311H"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:2:0:0"
    Option         "Rotate" "left"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 2560x1600 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Nick Payne on 2011-08-08
Well, rather than waste time trying to get 11.04 to work with both monitors, I installed 10.04, and with the same xorg.conf I have a fully functioning desktop working across both monitors.

Hopefully, by the time support for 10.04 finishes, these regressions might have been fixed.

It's pretty poor practice to release new versions of software with regressions from previous versions.

---

### Post by Magnes on 2011-08-09
> **Nick Payne said:**
> Well, rather than waste time trying to get 11.04 to work with both monitors, I installed 10.04, and with the same xorg.conf I have a fully functioning desktop working across both monitors.

Hopefully, by the time support for 10.04 finishes, these regressions might have been fixed.

It's pretty poor practice to release new versions of software with regressions from previous versions.

I wouldn't count on it. My configuration was working in 11.04 and have just been extremely broken after an update. :( They probably don't do any test for dual monitor support.

---

### Post by steve11911 on 2011-08-10
For those who wander here:
I appreciate the sentiment.My dual monitor issues were... interesting...(read: a few minor 4 letter words omitted...) Until  I found this exceptional ubuntu wiki page linked below:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

