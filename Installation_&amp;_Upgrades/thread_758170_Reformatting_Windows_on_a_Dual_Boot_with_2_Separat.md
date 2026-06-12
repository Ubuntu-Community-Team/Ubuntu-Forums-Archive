---
title: "Reformatting Windows on a Dual Boot with 2 Separate Hard Drives"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by rwartell on 2008-04-17
I have Grub running a dual boot on two separate hard drives.  On the one I'm running Ubuntu 7.10 and the other Windows XP.  XP has recently decided to go crazy and I need to reformat and reinstall it.  I'm not sure how to do this and preserve my set up with GRUB.  Does anyone have any advice?
       -Richard

---

### Post by Pumalite on 2008-04-17
This will give you an idea of what the problems are:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)
You can gto ahead and do it. XP will overwrite the MBR, but then you can reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by rwartell on 2008-04-17
When I reinstall GRUB, since my OS's are on two separate hard drives, GRUB will automatically detect and display my Ubuntu install on my second hard drive?  My main concern is losing my Ubuntu set up.

---

### Post by Pumalite on 2008-04-17
You will not loose Ubuntu if you don't format it. Make sure to backup everything before installing a new OS.

---

