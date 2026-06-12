---
title: "Upgrade to feisty?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Skeorx13 on 2007-06-08
I am currently running a dualbooted machine in windows XP and Ubuntu 6.10. I'm curious how many of you are running Feisty (7.04) and what problems you came across with upgrading to it. I heard a lot of horror stories (mainly with the Xserver) here and was curious if any issues have been sorted out yet. I already updated my crappy frankenstein monster PIII computer with no issues (one old 13" CRT, one small HD), but my main setup is more complicated. I have 6.10 (on one SATA hard drive) XP dualbooted (on a completely separate SATA hard drive) as well as a secondary IDE drive (also formatted to windows). I am running two LCD monitors of different sizes (19"-DVI and 15"-analog to DVI adapter) using the nvidia driver (and Twinview) with my GeForce 7600 GT XXX. I heard there was some transition issues with multiple monitors and I don't want to lose any data upon mounting the windows drives or any data from the xorg.conf file (as I painstakingly edited it almost entirely by hand, piece by piece). So does anyone have any knowledge to impart upon me? Things to watch out for? I plan to upgrade through the little orange popup button in gnome, but should I do this through the terminal instead?

---

### Post by pt123 on 2007-06-08
Here is my horror story : SATA Drives it doesn't recognise them. I didn't have problems with X much, but you need to change xorg.conf to nv from nvidia if it doesn't start. After that I had to install nvidia using the run package from the Nvidia site,  as Feisty's restricted nvidia drivers didn't work.

[http://ubuntuforums.org/showthread.php?p=2807672#post2807672](http://ubuntuforums.org/showthread.php?p=2807672#post2807672)

Anyway I have backed up by 6.10 installation so I will restore that, if this SATA mess doesn't get fixed. 

And then after that move back to Windows, because I loved 6.10 but I don't like the recklessness shown in the upgrades I am seeing in Ubuntu, and its future.

---

### Post by pt123 on 2007-06-08
[COLOR="DarkRed"][SIZE="4"]**Just an hour ago an Update to the Kernel arrived 2.6.20.16.29 that has fixed my problems with the SATA drives now all the drives are read as SDX. **[/SIZE][/COLOR]

I am so happy now, back in love with Ubuntu:D

---

