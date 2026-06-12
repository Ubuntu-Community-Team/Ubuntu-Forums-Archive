---
title: "Fail to Load Operating System"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by maxmingus on 2005-11-13
I tried to load the 64-bit version of Ubuntu onto my AMD 64 PC as a dual boot with Windoze XP, but after partitioning my primary drive and installing Ubuntu I get the message "Fail to load operating system" when I reboot. (I can't boot into either OS.)

When I run Linux from a live disk, my primary hard disk (a SATA drive) looks fine. I can see the partition with the win XP install with the files intact, plus the new linux and swap partitions. 

I know the problem must be with the MBR and Grub, but have no idea how to fix it.

Any help would be greatly appreciated,
Max

System specs
38 Gig SATA primary drive
60 Gig IDE secondary drive
Asus A8N-SLI motherboard
1 gig of memory
NVIDIA GeForce 6800 video card

---

### Post by taurus on 2005-11-13
What does your /boot/grub/menu.lst look like anyway???

---

### Post by tonysathre on 2005-11-13
try reinstalling grub, check out this link:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

---

