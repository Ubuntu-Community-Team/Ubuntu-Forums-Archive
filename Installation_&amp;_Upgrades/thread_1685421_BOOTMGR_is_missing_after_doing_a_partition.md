---
title: "BOOTMGR is missing after doing a partition"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by F8M on 2011-02-10
After looking at the following info, I noticed that my computer is arranged in a way to boot from 2 different drives(100Gig-Storage Drive and the 320Gig-Ubuntu/Partition Drive.
It should be arranged to boot from the 320Gig drive.

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69664f0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12162    97682420    7  HPFS/NTFS

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00012bcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81922443+  83  Linux
/dev/sda2           38165       38914     6013953    5  Extended
/dev/sda3           10200       38164   224628862+   7  HPFS/NTFS
/dev/sda5           38165       38914     6013952   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oldfred on 2011-02-10
BIOS controls booting. You set the default boot drive as the 320GB in BIOS.

Grub does not use boot flag, windows has to have one to know what partition to boot from.  But some BIOS require a boot flag on a primary partition to even start booting, so it is a good idea to alway have one per drive.

---

### Post by F8M on 2011-02-10
So, should I boot windows from the bigger drive and the Ubuntu from the smaller drive. Or, should I keep on trying to organize with what I have in mind to do with the bigger drive(Ubuntu/Wimdows partition) - and if so, how do I remove the booting in the 100Gig drive.

---

### Post by F8M on 2011-02-10
Ok, after looking at different ways to eliminate the storage drive booting sequence - here's what I did to resolve the problem. I reboot w/the Ubuntu Live CD and went into GParted to flag the Storage drive as "not bootable".
The following is what my partition looks like in the Gparted:

Partition                    File System                   Size  

unallocated                  unallocated                   1  MB
/dev/sda1                      ext 4                      78.13 GB
/dev/sda3                      ntfs                       214.22GB
unallocated                  unallocated                   4.49 MB
/dev/sda2                     extended                     5.74 GB
/dev/sda5                    linux-swap                    5.74 GB

Now that I have my BOOTMGR problem solved, how do I organize the above partition in the proper order. Thanks

---

### Post by oldfred on 2011-02-11
Partitions do not have to be in numerical order. 

If you create sda2 as the extended the logicals start at sda5 anyway. Then sda3 may be before or after sda2/sda5. The main rule is all logicals have to be inside the extended and primaries cannot be inside an extended.

Trying to move partitions around can create more problems. I would just leave it alone.

---

### Post by F8M on 2011-02-12
Thank you for your help.

---

