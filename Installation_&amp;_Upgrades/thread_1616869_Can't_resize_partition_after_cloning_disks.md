---
title: "Can't resize partition after cloning disks"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by wingnux on 2010-11-08
I bought an 1tb hard disk today and cloned my old 160gb ubuntu install to the new disk using gddrescue (from this tutorial [http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)) and everything worked fine. The problem is that I can't resize my home partition to fill the rest of the disk. I've tried using a live-cd and booting from my 160gb hard disk but I still can't resize the partition. 

Here's the "sudo fdisk -l" output:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009fac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1829    14690304   83  Linux
/dev/sda2            1830       19457   141596879+   5  Extended
/dev/sda5            1830        1891      497983+  82  Linux swap / Solaris
/dev/sda6            1892       19457   141098863+  83  Linux

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x822585ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7297    58613121    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009fac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        1829    14690304   83  Linux
/dev/sdd2            1830       19457   141596879+   5  Extended
/dev/sdd5            1830        1891      497983+  82  Linux swap / Solaris
/dev/sdd6            1892       19457   141098863+  83  Linux

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe9bfe9bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        3883        4865     7895947+   7  HPFS/NTFS
/dev/sdc2               1        3882    31180800   83  Linux

Partition table entries are not in disk order


Any help?

Thanks in advance!

---

### Post by coffeecat on 2010-11-08
I presume your home partition is sdd6. If so, the reason you can't enlarge it at the moment is simple. It's a logical partition "inside" the extended partition sdd2, and sdd5 and sdd6 together are completely filling sdd2. Enlarge sdd2 first to fill up the unallocated 782 GB space, and then you'll be able to resize sdd6 and also make more logical partitions inside sdd2 if you wish. Use the live CD or whatever installation is on sda. You may have to right-click on sdd5 and 'swapoff' if swap is on when using the live CD before you will be able to enlarge sdd2.

---

### Post by wingnux on 2010-11-08
Thank you VERY MUCH! That`s what I get for not wearing my contact lenses :P I could`t see the blue outline on the extended partition in order to resize it! Now everything is fine.

I can`t thank you enough!

---

