---
title: "Dual boot from BIOS Win7 &amp; Karmic"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by Indifferent on 2010-02-08
I would like to install grub or grub2 to my laptop's secondary hard drive (hd1 (sdb)) where Karmic is installed and be able to select the boot device from the BIOS Boot Menu <F12> that is available. During the installation of Karmic I did not select hd1 for Grub and it is now installed on hd0 (sda) where Win7 is installed.

I can reinstall the Win7 loader for sda, but I want to make sure that I can, and do, install grub to sdb properly.

If it helps: 2 x 500gb SATA HDD : Win7 64-bit (sda3) / Karmic PAE Kernel (sdb3) & ext4
fdisk info:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46ea46e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        1543      102400    7  HPFS/NTFS
/dev/sda3            1543       60802   475994136    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00012fcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         522     4192933+  82  Linux swap / Solaris
/dev/sdb2            6375       60801   437184877+   7  HPFS/NTFS
/dev/sdb3             523        6374    47006190   83  Linux

```
(not sure why the NTFS partition is shown as sdb2, it was created after the swap & ext4 partitions using gParted)
Any assistance is greatly appreciated.

---

