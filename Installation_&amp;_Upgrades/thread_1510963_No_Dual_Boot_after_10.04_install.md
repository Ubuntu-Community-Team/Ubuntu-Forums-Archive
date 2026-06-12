---
title: "No Dual Boot after 10.04 install"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by etxkesa on 2010-06-16
I have a PC with 3 hard disks, one IDE (30GB) plus two Sata (80 & 180 GB). The IDE is the disk master. Previously I had Ubuntu on the IDE disk, the smaller SATA for Windows XP and the larger SATA for all data. I recently decided to do a clean Windows install and thought that at the same time I'd swap the two OS disks. After I successfully installed the two systems (Ubuntu is Grub 2) I don't get any options presented at boot up. If I boot from hard disk and choose the IDE disk Windows books immediately.  If I try to change the disk boot order in the BIOS to choose the Ubuntu disk, nothing happens. Any idea how to get my dual boot back?

---

### Post by darkod on 2010-06-16
With multiple disks you need to double check where grub2 will get installed, and it also depends in which order you install the OSs (windows puts its bootloader to the disk first in the boot order so it might overwrite grub2 if you had the ubuntu disk as first when installing XP).

Things are obviously not where you expect them.

Set the ubuntu disk as first in boot order, but boot with the cd in live mode and post the result of

sudo fdisk -l

Once we know where the partitions are, we'll reinstall grub2 to the MBR of the ubuntu disk.

---

