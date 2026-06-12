---
title: "Multi-touch on touchpad"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by ferguson.stewart on 2014-01-17
I'm using Ubuntu 13.10 on my new Dell XPS 12 and I have problems with my touchpad multi-touch (2 finger scroll/swipe).  How can I enable this? I assume I need to install a driver.  I'm still quite new to this: 

Here's some info: 
```
stew@kronos:~$ xinput list
  Virtual core pointer
    -Virtual core XTEST pointer
    -DLL05E3:01 06CB:2734    <-- This is my touchpad
    -ATML1000:00 03EB:842F
    - PS/2 Generic Mouse
   Virtual core keyboard
   ...

stew@kronos:~$ sudo trackpad show
  sudo: trackpad: command not found
stew@kronos:~$ sudo synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?
```

My "Mouse & Touchpad" section of "All Settings" just shows: 
Primary button : o Left,  o Right
Double-click : Slow[-----------------------------]Fast
Pointer speed: Slow[----------------------------]Fast

Oh, and my system has no /etc/X11/xorg.conf.  Not sure if that's a problem. Would I have to generate one of these to select a driver?

---

### Post by ferguson.stewart on 2014-01-17
FYI,  I've also tried:
1/ gpointing-device-settings, but it didn't add any functionality.

2/ Adding: ppa:sergio91pt/synaptics+clickpads and sudo apt-get dist-upgrade, but the ppa 404'd.

3/ Installing synaptiks to manage my device, but it told me that the drivers were not installed.

My X11 stuff is in /usr/share/X11/xorg.conf.d/ but there are so many files there, that I can't tell which ones are active.

---

### Post by ferguson.stewart on 2014-01-17
I found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1218973](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1218973)
Does this mean that I need to wait for a new release of the kernel?  It desribes my problem EXACTLEY.

---

