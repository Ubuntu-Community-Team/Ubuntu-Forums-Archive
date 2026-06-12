---
title: "How do I add a custom resolution with the new xorg?"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by denzilla on 2009-04-12
Running 9.04 inside VirtualBox and it doesn't list my LCDs rez of 1280x1024. How can I manually add this?

---

### Post by caryb on 2009-04-12
If you edit /etc/X11/xorg.conf

& look for..


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    [COLOR="Red"]Modes	    "1024x768"
    Virtual         1024 768[/COLOR]
EndSection

add the red lines to suit your resolution

Cary

---

### Post by denzilla on 2009-04-13
There are no such entries in my xorg.conf. Does it being in VM have anything to do with that?

---

### Post by Zorael on 2009-04-13
xorg.conf is pretty empty by default nowadays; most configuration is done automatically by HAL. See [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) though.

---

