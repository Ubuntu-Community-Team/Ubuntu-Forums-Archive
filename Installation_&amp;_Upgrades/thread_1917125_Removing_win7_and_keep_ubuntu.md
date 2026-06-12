---
title: "Removing win7 and keep ubuntu"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by matza55 on 2012-01-29
Hi, I tired of win7, so now it's time to remove it. How is the best way to remove it, and have a option to start with the right os (boot)? I have win 7 + 3 other distros (UE, Mint & Ubuntu 11.10) Change grub?

mats@mats-ultraedition ~ $ sudo fdisk -l
[sudo] password for mats: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0077741

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          13        4256    34076672    7  HPFS/NTFS
/dev/sda3            4256       38914   278389761    5  Extended
/dev/sda5            4256        9128    39132160   83  Linux
/dev/sda6            9128        9857     5858304   82  Linux swap / Solaris
/dev/sda7            9857       14598    38084608   83  Linux
/dev/sda8           14599       19462    39061504   83  Linux
/dev/sda9           38392       38914     4192256   82  Linux swap / Solaris
/dev/sda10          19462       23960    36131840   83  Linux
/dev/sda11          23960       26477    20216832   83  Linux

Partition table entries are not in disk order

---

### Post by darkod on 2012-01-29
If you are using grub1/grub2 on your MBR to boot with, you can simply boot ubuntu and open Gparted, delete the win7 partitions and that's it. Copy any data you need from win7 first.

After that simply adjust grub not to show the win7 entry. For grub1 you will need to edit the menu.lst and for grub2 it's enough to simply run in terminal:
sudo update-grub

---

