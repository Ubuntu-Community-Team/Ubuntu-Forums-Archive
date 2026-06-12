---
title: "[SOLVED] GRUB Error 22"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by Gannon8 on 2008-03-18
I tried out Kubuntu after installing Ubuntu. I liked Kubuntu better, so I made a partition for Kubuntu and deleted the Ubuntu partition (saving space so when I find windows disk to reinstall it so I can play Continuum again). Now, when I boot my computer, it gives me GRUB Error 22. I searched the forums, but to no avail. Is there a way to fix this? I am in Kubuntu live CD and typing this on my mom's laptop, where we are on vacation in a small house with REALLY slow dial-up :sad:

---

### Post by logos34 on 2008-03-19
Reinstall grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Sef on 2008-03-19
This is GRUB error 22:

> No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

If logos34's suggestion does not work, then using the live cd, open a terminal (Konsole, i think in Kubuntu) and type this command:

> sudo fdisk -l Small L

It will show what partitions that you have on your hard disk.

---

### Post by Gannon8 on 2008-03-19
Yay it works!
When I did this, the error message was error 17, but this fixed it. Thanks!

---

