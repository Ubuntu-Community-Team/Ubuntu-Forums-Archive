---
title: "eternal harddrive after updating to feisty"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by siehtschlecht on 2007-04-03
I have updated to feisty. After that my external hard drive on usb isn´t there anymore. In edgy it was mounted properly.
In my fdisk i can see it (depending on the usb-port) in /dev/sdb:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2431    19526976    7  HPFS/NTFS
/dev/hda2            4221        4864     5172930    f  W95 Ext'd (LBA)
/dev/hda3            2432        4220    14370142+  83  Linux
/dev/hda5            4302        4864     4522266    b  W95 FAT32
/dev/hda6            4221        4301      650569+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12161    97683201    b  W95 FAT32

Can anyone help.

p.s. Did anyone know how to view google-videos after updating to feisty?

---

### Post by siehtschlecht on 2007-04-08
No idea anyone?
It seems, I1m not the only one with this problem.
My external HD is not autodetect/automount from usb. The HD has nor partitions. In Windows there is no problem. Even after a check in windows nothing changed. 
In the fstab i can see it. Everytime i have to manually mount. With usb-Sticks i have no problem. They get the icon on the desktop and i can mount and unmount them with a right-mouse-click.
What is the problem with the HD?
Pleas help.

---

