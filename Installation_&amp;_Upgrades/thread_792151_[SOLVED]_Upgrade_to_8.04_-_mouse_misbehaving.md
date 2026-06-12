---
title: "[SOLVED] Upgrade to 8.04 - mouse misbehaving"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by shinyone on 2008-05-12
I have just upgraded to 8.04. The upgrade process was seamless (though due to a problem with my adept-manager I had to update on the command line with do-release-upgrade).

However, now that I've upgraded my mouse is misbehaving. My best guess is that each click is being registered as a double click. The symptoms I'm seeing are:
- Clicking text highlights a word / section (depending on the app)
- Menus and Bookmark folders in Firefox do not open
- Menus in other apps are very hard to open and keep open
- Highlighting an email in Thunderbird causes it to open in a new window

I haven't changed any settings since I upgraded, and I never had any problems before. I upgraded from 7.10 (all packages were at latest version before I upgraded).


Anyone able to offer some advice?



(Potentially) relevant sections in xorg.conf:

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    #   Option      "CorePointer"
    Option      "Device"    "/dev/input/mice"
    Option      "Protocol"  "ImPS/2"
    Option      "ZAxisMapping"  "4 5"
    Option      "Emulate3Buttons"   "true"
EndSection
Section "ServerLayout"
    Identifier  "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
    Inputdevice "Generic Keyboard"
    Inputdevice "Configured Mouse"
EndSection
Section "Module"
    Load        "dbe"
    Load        "v4l"
EndSection
Section "Extensions"
    Option      "Composite" "0"
EndSection
Section "ServerFlags"
    Option      "Xinerama"  "true"
EndSection



Xorg.0.log:

[...]
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Philips 190S"
(**) |   |-->Device "0 Generic Video Card"
(**) |-->Screen "screen1" (1)
(**) |   |-->Monitor "monitor1"
(**) |   |-->Device "1 Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) Option "Xinerama" "true"
(==) Automatically adding devices
(==) Automatically enabling devices
(**) Xinerama: enabled
[...]
(**) Extension "Composite" is disabled
(==) |-->Input Device "Configured Mouse"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first mouse device.
(II) Open ACPI successful (/var/run/acpid.socket)
[...]
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.47.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.471
(II) ATI Proprietary Linux Driver Build Date: Feb 25 2008 21:22:09

---

### Post by shinyone on 2008-05-12
xev output (from a single click):


ButtonPress event, serial 32, synthetic NO, window 0x3200001,
    root 0xe9, subw 0x0, time 2293812, (141,68), root:(260,861),
    state 0x0, button 1, same_screen YES

ButtonPress event, serial 32, synthetic NO, window 0x3200001,
    root 0xe9, subw 0x0, time 2293812, (141,68), root:(260,861),
    state 0x100, button 1, same_screen YES

PropertyNotify event, serial 32, synthetic NO, window 0x3200001,
    atom 0x151 (_KDE_WM_WINDOW_OPACITY), time 2293813, state PropertyDelete

ButtonRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0xe9, subw 0x0, time 2293905, (141,68), root:(260,861),
    state 0x100, button 1, same_screen YES

ButtonRelease event, serial 32, synthetic NO, window 0x3200001,
    root 0xe9, subw 0x0, time 2293905, (141,68), root:(260,861),
    state 0x0, button 1, same_screen YES

---

### Post by shinyone on 2008-05-12
Update: I managed to completely break my xorg.conf file and had to rewrite it from scratch based one generated from the system-settings tool. It works now, but I have no idea what has changed.

I will mark this as solved, but I can't really explain what happened or why it is now fixed.

Old and new conf files are attached if anyone is interested to take a look.

---

