---
title: "Tap touchpad doesn't work after upgrade on Ubuntu 16.10"
date: 2016-11-19
forum: Installation &amp; Upgrades
---

### Post by Bozoo on 2016-11-19
Hi, 
After trouble with my resolution & dnsmasq ....
My touchpad does not work completely.
Tap on touchpad is broken ...
I try this it solve by an echec : 
```

UX301LAB:~$ synclient tapbutton1=1
Couldn't find synaptics properties. No synaptics driver loaded?

```

```

 sudo libinput-list-devices 
Device:           Power Button
Kernel:           /dev/input/event2
Group:            1
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a


Device:           Video Bus
Kernel:           /dev/input/event4
Group:            2
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a


Device:           Sleep Button
Kernel:           /dev/input/event1
Group:            3
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a


Device:           HD WebCam
Kernel:           /dev/input/event12
Group:            4
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a


Device:           Atmel Atmel maXTouch Digitizer
Kernel:           /dev/input/event10
Group:            5
Seat:             seat0, default
Size:             307.10x161.63mm
Capabilities:     touch 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      identity matrix
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a


Device:           Asus WMI hotkeys
Kernel:           /dev/input/event11
Group:            6
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a


Device:           AT Translated Set 2 keyboard
Kernel:           /dev/input/event3
Group:            7
Seat:             seat0, default
Capabilities:     keyboard 
Tap-to-click:     n/a
Tap-and-drag:     n/a
Tap drag lock:    n/a
Left-handed:      n/a
Nat.scrolling:    n/a
Middle emulation: n/a
Calibration:      n/a
Scroll methods:   none
Click methods:    none
Disable-w-typing: n/a
Accel profiles:   n/a
Rotation:         n/a


Device:           ETPS/2 Elantech Touchpad
Kernel:           /dev/input/event5
Group:            8
Seat:             seat0, default
Size:             92.50x60.12mm
Capabilities:     pointer 
Tap-to-click:     disabled
Tap-and-drag:     enabled
Tap drag lock:    disabled
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *two-finger edge 
Click methods:    *button-areas clickfinger 
Disable-w-typing: enabled
Accel profiles:   none
Rotation:         n/a

```
Thank's for your help.

---

