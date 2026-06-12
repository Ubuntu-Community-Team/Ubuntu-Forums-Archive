---
title: "Cannot start X server with ATI AX800 graphics card"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by david25520 on 2006-09-29
I used the Dapper Drake 6.06.1 install CD to install ubuntu because the standard CD would not boot on my i386 computer (failed to start the X Server). Next, since I have an ATI AX800 graphics card, I installed the fglrx driver, but after running the dpkg-reconfigure xserver-xorg command I still cannot get the X Server to start correctly (I get a gray screen). At one point I even tried the vesa driver but that did not work (also gray screen).

My /var/log/Xorg.0.log file ends with a series of errors (xf860OpenSerial: Cannot open device /dev/wacom) although I do not believe this is related.

Also, what is required to start gdm automatically?

---

### Post by summoness on 2006-09-29
i use x1300 and just use aticonfig --initial
then since i have two monitors  aticonfig --dtop=horizontal
and i have a xinerama setup with fglrx I get approx 2800 fps with glxgears

---

