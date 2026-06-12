---
title: "Getting Grub Error 18"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Rocky44 on 2007-08-30
I've just installed Ubuntu off of the Live CD, and when I try to start it up, I get Grub Error 18.  
What I've done is reinstalled Ubuntu several times, and I've gone into bios to try to change my LGA mode (I think) to normal, but I can't, because it's grey'd out, and I can't edit it.  If someone can help me fix this, I would greatly appreciate it.  One other thing, I'm trying to install Ubuntu on a slave drive, if that effects anything.

---

### Post by fish2ways on 2007-08-30
Never encountered this myself but here are a couple of links that may help. 

[http://www.linuxforums.org/forum/debian-linux-help/52256-first-time-trying-linux-grub-error-18-a.html](http://www.linuxforums.org/forum/debian-linux-help/52256-first-time-trying-linux-grub-error-18-a.html)
[http://ubuntuforums.org/archive/index.php/t-77042.html](http://ubuntuforums.org/archive/index.php/t-77042.html)
 From the Gentoo Handbook

6. Grub Error 18

Situation

Code Listing 6.1: Grub Output

kernel (hd1,4)/bzImage root=/dev/hdb7

Error 18: Selected cylinder exceeds max supported by BIOS

Solution

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range).

Hope this helps.

---

