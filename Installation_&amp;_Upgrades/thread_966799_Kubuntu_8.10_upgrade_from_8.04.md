---
title: "Kubuntu 8.10 upgrade from 8.04"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Mhurst1 on 2008-11-01
I tried to upgrade Kubuntu 8.04 to 8.10 and it seemed to go well, but when I rebooted I just get a blank screen please help.

---

### Post by lemming465 on 2008-11-02
You probably have an X driver issue with your video chip; 8.10 has some problems with both ATI and Nvidia in some circumstances.

First thing is see if the failsafe boot gets you video.

If not, try [Ctrl-Alt-F2] to get a text console, and see what error messages are in /var/log/Xorg.0.log.

If you can specify your video hardware in more detail, we can offer more specific advice.

For ATI, try converting to xserver-xorg-driver-flgrx
For Nvidia, try converting to xserver-xorg-driver-nv

Putting *driver "vesa"* /etc/X11/xorg.conf is a more permanent version of the failsafe boot.

---

