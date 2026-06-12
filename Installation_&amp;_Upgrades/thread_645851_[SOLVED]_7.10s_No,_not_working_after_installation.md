---
title: "[SOLVED] 7.10s? No, not working after installation"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by g0kb3rk on 2007-12-20
I have downloaded the 7.10 versions of Ubuntu and Kubuntu but there is one thing common in my problems with both distros. I can run them as a Live CD, do whatever I can and install however I want on my laptop. Ubuntu 7.04 was working smooth on it but now 7.10 versions of both distros  aren't working. The problem is when I finish the installation and reboot the system a white screen comes out and never leaves until I turn my laptop. When I turn on my PC, after GRUB nothing happens, same for the rescue.

I [posted a thread]("http://ubuntuforums.org/showthread.php?t=590305") about it -and totally forgot it- but the given advices -I'm not mad or something else about them- made the same thing happened. I can't think of any possibilities because while earlier Ubuntu version is working quite well. Here is my laptop hardware.

Intel Centrino 1.8 GHZ
512 MBs of RAM, shared 128 MBs with Ati Radeon Mobility 9500
TSST Corp DVD Rom, CD Writer
60 GBs of HDD, 11 GB given for Linux, 150 MB for swap
Wireless, ethernet etc. :)

EDIT : I can run on the recovery mode and login to my account and start X but how can I fix this problem? I want it to start like usual.
EDIT2 : CTRL+ALT+F1 shows the white screen too

---

### Post by Pumalite on 2007-12-20
Try the Alternate CD.

---

### Post by g0kb3rk on 2007-12-21
Thanks man, Kubuntu is working now but I have 2 questions again :) :?

How can I install Last.Fm, Firefox etc.? They are unselectable in Adept Installer (I searched the whole forum but couldn't find it)

---

### Post by Pumalite on 2007-12-21
You can download the latest Firefox from their site to your Desktop. Then, at the Terminal:
cd ~/Desktop
tar xvzf firefox-2.0.0.11.tar.gz
cd firefox
./firefox
Make sure Firefox is closed when you do this.

---

### Post by g0kb3rk on 2007-12-21
just fixed it after the reply. Thanks man, it is now working smoothly.

---

### Post by Pumalite on 2007-12-21
You are welcome. Good luck!

---

