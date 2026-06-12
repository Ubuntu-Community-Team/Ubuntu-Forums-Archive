---
title: "Kernel-panic at boot up (lubuntu xfce 15.04)"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by Just_Someone on 2015-10-14
Well ive got some old laptop an older acer travelmate
now i installed lubuntu 15.04 on the hard drive since the live usb worked fine and even the wifi-driver was fine aswell.
Now i booted it up for the first time (so after install)
and i got the following code while starting up:
why? plz help me i installed lubuntu 15.04 64 bit btw bcs linuxmint xfce didnt work at 32 bit and windows 8 (64bit) also just runs fine
[IMG]http://i.imgur.com/v2gV3Hy.jpg[/IMG]

i know there is no default lubuntu xfce but i switched it up in my head bcs i wanted to tell you guys that i tried linuxmint xfce there is ofcourse no (DEFAULT) lubuntu

---

### Post by ian-weisser on 2015-10-17
It's in the error message "No working init found. Try passing init= option"
The initramfs kernel is trying to load init on your hard drive...and can't find it, so it crashes.

There are many possible causes for it.
Could be an installer error, a partitioning mistake, a cloning mistake, a dual-boot error caused by Windows or boot-repair, etc.

A bit of search-engine research will probably help you narrow  the possible causes on your system.

---

