---
title: "Dual boot issue (XP) - Can't boot after install"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by LaxJack on 2008-03-19
Hi.

I've installed ubuntu 7.10 on a spare 20GB non-system IDE disk on my PC running XP with both my Windows system disk and this spare disk connected.  Everything seemed to install smoothly but when it rebooted after install I got "GRUB loading " and then "error 17". This happens whenever I try booting from this disk and now can't boot from my Windows disk too. My wife is gonna kill me for stuffing this up. 

I've tried digesting information at [https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28dual%29%7C%28boot%29](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28dual%29%7C%28boot%29) but my menu.lst file is empty and fdisk -l returns the following

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        9725    78083932+   7  HPFS/NTFS

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90af06d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f32cbb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

Windows is on sda2 and I'm not sure what to do next as this is my first taste of Unix. I would really appreciate any guidance anyone can provide.

---

### Post by neerajadsul on 2008-03-19
Try this thread -
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by LaxJack on 2008-03-19
Many thanks - that seems to have fixed it.

---

