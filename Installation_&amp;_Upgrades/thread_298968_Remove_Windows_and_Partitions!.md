---
title: "Remove Windows and Partitions!"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by DimitrisC on 2006-11-13
The screenshot below shows my partition configuration on my laptop. The first small partition is the Dell Recovery Partition (i don't need it). Then is the ntfs (windows installation) and a fat32 for backup. The rest as you can see is my ubuntu installation.
I want to now if it is possible to delete all other partitions and resizing my linux partition to take up the whole free space created leaving my system with 2 partitions only (swap and linux partition).  I want to do this without destroying my existing linux installation (a lot of effort went into getting things working and i want to avoid doing it all over again).  If this is possible will grub see the changes and keep my linux partition bootable or do i have to do any changes?

Thanks in advance!!!

---

### Post by earobinson on 2006-11-13
you should be able to do this, but you may need a live cd (im not sure if ubuntu will let you resize a partition in use)

Grub will not change you will need to manualy remove your windows boot from /boot/grub/menu.lst

---

