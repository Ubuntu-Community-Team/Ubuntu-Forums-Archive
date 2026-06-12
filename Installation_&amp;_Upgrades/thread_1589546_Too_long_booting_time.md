---
title: "Too long booting time"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by zipeppe on 2010-10-06
Hi guys,

Ubuntu 10.10rc, fresh installation for my desktop PC.


The following partition have been successfully installed:

/dev/sde1 on /boot type ext3
/dev/sde2 on /     type ext4
/dev/sdd3 on /home type ext4
/dev/sdd5 on /opt  type ext4 

The problem is related to the boot process: it takes about 150 seconds before becoming ready. To me it seems that the problem is related somewhat to the sde disk, but it was checked by using the fsck program, without reporting any error.

After the grub passes the control to the kernel, I see that the monitor switches through different resolutions several times, but it remains black (I mean: none console information is prompted to the terminal even if the [ESC] key is pressed) for 60-70 seconds; then the desktop background loads, but it waits for 60-70 seconds before asking for the login.

Once logged in the system, everything works perfectly. Seriously: no problem at all! 
Even the shutdown procedure is impressively fast: less than 5 seconds to powering off the PC.

So, what I have to check to fix this issue?

In attachment there are:

output **dmesg** command
output **lspci -v** command
file **/etc/default/grub**

And this is the output of the **sudo fdisk -l** command:

```

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa65be34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        7648    30716280    7  HPFS/NTFS
/dev/sda3            7649       11472    30716280    7  HPFS/NTFS
/dev/sda4           11473       15017    28475212+   7  HPFS/NTFS

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe0917ea8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          32      257008+  83  Linux
/dev/sdb2              33         293     2096482+  82  Linux swap / Solaris
/dev/sdb3             294       15017   118270530   8e  Linux LVM

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dae92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdc2              14         138     1004062+  82  Linux swap / Solaris
/dev/sdc3             139         443     2449912+  fd  Linux raid autodetect
/dev/sdc4             444       19457   152729955    5  Extended
/dev/sdc5             444        1052     4891761   fd  Linux raid autodetect
/dev/sdc6            1053        1661     4891761   fd  Linux raid autodetect
/dev/sdc7            1662        1844     1469916   fd  Linux raid autodetect
/dev/sdc8            1845        2149     2449881   fd  Linux raid autodetect
/dev/sdc9            2150        2758     4891761   fd  Linux raid autodetect
/dev/sdc10           2759       19457   134134686   fd  Linux raid autodetect

Disk /dev/dm-0: 57.5 GB, 57512296448 bytes
255 heads, 63 sectors/track, 6992 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 2281 MB, 2281701376 bytes
255 heads, 63 sectors/track, 277 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 38.7 GB, 38654705664 bytes
255 heads, 63 sectors/track, 4699 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06dc06db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         255     2048256   82  Linux swap / Solaris
/dev/sdd3             256        5118    39062047+  83  Linux
/dev/sdd4            5119       19457   115177987    5  Extended
/dev/sdd5            5119        9981    39062016   83  Linux
/dev/sdd6            9982       14844    39062016   83  Linux
/dev/sdd7           14845       19457    37053891   83  Linux

Disk /dev/md6: 5009 MB, 5009047552 bytes
2 heads, 4 sectors/track, 1222912 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md6 doesn't contain a valid partition table

Disk /dev/md5: 2508 MB, 2508587008 bytes
2 heads, 4 sectors/track, 612448 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md5 doesn't contain a valid partition table

Disk /dev/md0: 106 MB, 106823680 bytes
2 heads, 4 sectors/track, 26080 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md3: 5009 MB, 5009047552 bytes
2 heads, 4 sectors/track, 1222912 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md3 doesn't contain a valid partition table

Disk /dev/md2: 5009 MB, 5009047552 bytes
2 heads, 4 sectors/track, 1222912 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table

Disk /dev/md1: 2508 MB, 2508587008 bytes
2 heads, 4 sectors/track, 612448 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md4: 1505 MB, 1505099776 bytes
2 heads, 4 sectors/track, 367456 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md4 doesn't contain a valid partition table

Disk /dev/md7: 137.4 GB, 137353822208 bytes
2 heads, 4 sectors/track, 33533648 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md7 doesn't contain a valid partition table

Disk /dev/sde: 36.4 GB, 36401479680 bytes
255 heads, 63 sectors/track, 4425 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x184d184c

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          31      248976   83  Linux
/dev/sde2              32        4425    35294805   83  Linux


```


That's makes me crazy :confused:

Maybe a problem related to the SCSI Adapter? 
Googling around the "mptscsih attempting task abort" message, the problem seems related to the kernel/controller activities, and those are the guys:

03:03.0 SCSI storage controller: Marvell Technology Group Ltd. MV88SX6041 4-port SATA II PCI-X Controller (rev 07)
04:03.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07)
04:03.1 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07)


Please, gimmi a light!

---

