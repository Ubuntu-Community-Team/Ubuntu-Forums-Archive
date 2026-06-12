---
title: "Feisty with RAID - does not work"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by nicolasdiogo on 2007-06-21
hi folks,

i am trying to install Ubuntu feisty with RAID 1 with the ALTERNATIVE CD;
and after following various posts on the web i have come to a dead end.

i have two hd sata2, same maker, model and size (80gb).  And create the following partition in both disks:
1 gb - /boot
1 gb- swap
20 gb - / (root)
58 gb - /var

so the idea of having:

/dev/md1 => /dev/sda1 /dev/sdb1
/dev/md2 => /dev/sda2 /dev/sdb2
/dev/md0 => /dev/sda3 /dev/sdb3    root
/dev/md4 => /dev/sda4 /dev/sdb4

fails when an IO error happens in what seems to be the same point in the disk.

i have checked the output of cat /proc/mdstat and it fails on 25.4% when creating the md0.

how can i check if there is an error on the disks before i try to install the software?

many thanks,

Nicolas

---

