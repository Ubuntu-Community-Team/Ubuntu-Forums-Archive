---
title: "Reboot during live cd install"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by Schradman on 2008-03-24
I'm trying to install 7.10 using the live CD.

My system specs are:
Intel Core 2 Quad Q6600 2.4GHz
NVIDIA 8500GT
4GB of DDR2 800 RAM

When I try to use the options "Start or Install Ubuntu" or "Start Ubuntu in safe graphics mode" it will start to load the kernel then display:
"Kernel Alive"
"Kernel ... mapping tables ..." (Don't exactly remember this message)

Then the screen will go black and then eventually my machine will reboot. I've successfully booted to the live cd of ubuntu once. The screen was black for awhile then it finally booted to ubuntu. Ever since then it will just reboot. :mad:

I've tried 2 different cds.

---

### Post by Rocket2DMn on 2008-03-24
The LiveCD does not work for everybody, often because of video driver issues.  You should try the Alternate install cd, available at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.  It uses a text based installer rather than a live session, but it is very easy and intuitive to use.  Once you have Ubuntu installed, your video card should work fine with the restricted nvidia drivers.

---

### Post by Schradman on 2008-03-24
I downloaded the alternate version and began the install. Now the install fails when trying to mount the CD-ROM drive. I have a SATA Lite-ON DVD+RW.

---

### Post by Rocket2DMn on 2008-03-24
What do you mean?  Did you actually get to the install process?
You should check the md5sum on the cd
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against.
Then burn the disc at a slow speed like 4x to prevent write errors.
Perhaps you can take a picture of where it is failing, because I don't understand how it's failing to mount the cd drive, that shouldn't even be necessary during install (you're already booted from the disc).

---

