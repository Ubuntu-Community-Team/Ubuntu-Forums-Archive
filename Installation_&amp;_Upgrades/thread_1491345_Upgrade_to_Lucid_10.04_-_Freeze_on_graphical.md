---
title: "Upgrade to Lucid 10.04 - Freeze on graphical"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by rcbell on 2010-05-23
Hi 

After running 9.10 (Kubuntu) uneventfully on my Thinkpad x100e (chip: AMD Neo MV-40, graphics: Radeon HD 3200), I upgraded to Lucid and am getting a system freeze/hang.

I'm running the Xorg radeon driver.

At first the freeze was on the KDM login screen, right after the audio drumbeats.  I upgraded the BIOS to the latest from Lenovo, and now I can log in, but it freezes right away while trying to build the desktop.  I've tried the failsafe graphical boot, and all I get is a black screen.

Any suggestions? I've seen some threads related to the i845/i855 chips, but that shouldn't be an issue here (although I tried some of the workarounds which didn't help).  I'd like to avoid the fglrx driver if I can, but I'll give that a shot if I can't get past this.

Thanks!
Disappointed

---

### Post by rcbell on 2010-05-23
OK, I found a workaround in this thread:
[INDENT][http://swiss.ubuntuforums.org/showthread.php?p=9210552](http://swiss.ubuntuforums.org/showthread.php?p=9210552)
[/INDENT]The trick was to boot with "radeon.modeset=0" 

There's already a similar bug reported,
[INDENT][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535653)
[/INDENT]but the symptoms on that bug are that it only happens on battery power.  My freeze occurred with it the power cord plugged in.

---

