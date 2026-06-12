---
title: "error 17: cannot mount selected partition"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by pzdc on 2008-06-12
I installed ubuntu 64 bit on 120 gig HDD and when starting Ubuntu I get this error:

error 17: cannot mount selected partition

the output of fdisk is here:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6527e853

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91201   732572001    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68745c24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1938    15566953+   7  HPFS/NTFS
/dev/sdb2   *        1939       11500    76806765    7  HPFS/NTFS
/dev/sdb3           11501       91201   640198282+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803435    5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17ac17ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30400   244187968+   7  HPFS/NTFS





How do I fix this? :confused::confused:

---

### Post by Pumalite on 2008-06-12
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
You might have a mix of SATA and IDE and Grub is trying to boot the IDE drive. Boot your Live CD and check your menu.lst

---

