---
title: "gparted does not see windows partitions."
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by hayati on 2006-08-25
i have acer aspire 1694wlmi and xp already installed on a partition. it has 2 more windows partitions. When i boot with Dapper LiveCD Disk-admin sees them all right but gparted says that it's all "unallocated". this is wrong info. when i press next without any allocation it sees partitions but this time it says "you need to specify a root directory". Specifying a root directory requires to write mbr which is very risky.

-----------------------------------------------------------------------------------
some body had the same problem before as below
-----------------------------------------------------------------------------------




Binary package hint: gparted

I've just installed DapperRC on an AMD box with two hard disk drives, I used the LiveCD and gparted to partition the first hard disk and I installed XP on it, then again I booted the LiveCD and installed Dapper on the second disk. The problem is that gparted doesn't recognize the Windows partitions and the swap partition it created on the first disk: it simply says "Type of disk: not recognized" and all the disk space is tagged as "unallocated". Note that disks-admin sees them all right, and in fact I successfully added them to fstab (can access them fine). Same goes for fdisk:

sudo fdisk -l /dev/hda

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot Start End Blocks Id System
/dev/hda1 * 1 2611 20972826 7 HPFS/NTFS
/dev/hda2 2612 5222 20972857+ 7 HPFS/NTFS
/dev/hda3 5223 19929 118133977+ 5 Esteso
/dev/hda4 5745 19929 113941012+ b W95 FAT32
/dev/hda5 5223 5744 4192902 82 Linux swap / Solaris

This is on an AMD Sempron 3100 box, the disks are two brand new SATA 160 GB Maxtor drives, CPU is an AMD Sempron 3100, GPU an ATI Sapphire Radeon 9550.

---

### Post by mod187 on 2006-08-25
I tried running gparted from the ubuntu live CD, and had problems with it finding all of my drives correctly. The gparted live CD is much better, and may help you with your problem.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

