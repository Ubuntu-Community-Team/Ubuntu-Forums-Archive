---
title: "please help with this install problem"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by iispyderii on 2008-01-13
i need some major help.

i was going to install the i386 desktop ubuntu 7.10
i was going untill i got to the partitioning part. it was manual partition. i said make new partition on the main hdd for about 2GB and it started and then it said it had an error! it reformatted the whole hdd and now i have nothing. the only thing that the computer will do is go to bios or either i can boot the Ubuntu Live CD.

so is there anyway to recover the whole hdd files (i did find my windows xp home edition)
so i need a program one can run from a bios or from linux so i can unformat the hdd.

here's my fdisk -l

> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 * 6 4437 35600040 b W95 FAT32
/dev/sda3 4438 4863 3421845 db CP/M / CTOS / ...

thanks for the help!

---

### Post by Pumalite on 2008-01-13
Mount sda2 and see if there is anything there.
At the Terminal:
sudo mkdir /media/sda2
sudo mount -t vfat /dev/sda2 /media/sda2

---

