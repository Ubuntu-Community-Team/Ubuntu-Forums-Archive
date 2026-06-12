---
title: "Can't install/boot Ubuntu--'no screens found' error"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by zhinker on 2007-04-19
Hi, I'm having a tough time getting Ubuntu to work on my computer (most likely caused by my Radeon X600 video card).  I managed to dualboot install Ubuntu 6.06 on my computer using the alternate CD a while back (because at the time this noob thought it might be more compatible than the 6.10 alternate CD), but I kept on getting the error 
"Fatal server error: No screens found"
whenever I tried to run Ubuntu.  I get the same error with all the newer live CD's as well.  

These are the relevant stats the error screen showed:
X Window System version 7.0.0
X Protocol Version 11, Revision 0, Release 7.0

Those are probably out of date, but I can't figure out how to get a newer version installed.  

Right now I've downloaded the 7.04 alternate CD, but I'd like to get some advice before I actually install it

Any and all help is greatly appreciated!

---

### Post by sharke on 2007-04-20
At the command prompt
sudo aptitude install xorg-driver-fglrx
Then
sudo dpkg-reconfigure xserver-xorg

Select the fglrx driver and complete reconfigure reboot and you should be sweet.

Regards
Sharke

---

### Post by zhinker on 2007-04-20
Dude, you are a godsend!  I've been trying to get Linux to work on my computer since December!

---

### Post by sharke on 2007-04-20
> **zhinker said:**
> Dude, you are a godsend!  I've been trying to get Linux to work on my computer since December!
Im Glad it worked.
Regards
Sharke

---

