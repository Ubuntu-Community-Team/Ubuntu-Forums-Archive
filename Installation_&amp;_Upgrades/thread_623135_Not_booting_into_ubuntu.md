---
title: "Not booting into ubuntu"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by corcaigh on 2007-11-25
Hi i was installing 7.04 on my pc from live cd. I wanted to keep xp so i let it install grub. It all seemed to install fine but after it restarted it went straight into xp again. It said that it installed grub, so i have no idea whats wrong.

---

### Post by Pumalite on 2007-11-25
Boot a Live CD and post:
sudo fdisk -lu
Your specs would help too. And what iso did you use?

---

### Post by corcaigh on 2007-11-25
Sorry mate. I'm using a 4200x2, 2 gigs of ram and nvidia 7800gt. I used the official cd got it a few months ago.
These are results i got with command:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63   149790059    74894998+  83  Linux
/dev/hdc2       149790060   156248189     3229065    5  Extended
/dev/hdc5       149790123   156248189     3229033+  82  Linux swap / Solaris

---

### Post by Pumalite on 2007-11-25
Do you have a mix of SATA and IDE?
Try reinstalling Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by corcaigh on 2007-11-25
Ya i do will try with that app. Thanks very much.

---

### Post by meierfra on 2007-11-25
See what happens if you change the boot order in the bios.

---

### Post by corcaigh on 2007-11-25
Followed the method in that thread but it just didn't seem to work out. Is there any method i could get ubuntu to boot via boot.ini or something?

---

### Post by Pumalite on 2007-11-25
If you have mix of SATA and IDE, read this:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by meierfra on 2007-11-25
Did you try changing the boot order? It might not solve your problem immmediately,  but at least it should give some information on what is really going on.

---

