---
title: "Hardy-how do I replace a second, modified, XP HD?"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2008-06-08
Hi,
Currently I'm on a dual Hardy/XP system with 2 SATA drives: sda (several partitions) used for XP and Linux swap,and sdb-used for Linux-Hardy Kubuntu.Being an avid photographer, using several XP-based photo-manipulation programs, I still need XP. As I ran out of disk space on my XP disk-lots of pictures which I keep (+ aging XP), I've bought a new, large sata2 HD to replace my sda. Besides the different size, I plan to arrange my new sda differently with only 3 primary partitions as follows:

sda1- single XP partition  ("C")
sda2 -  XP images, created by partimage (reizer3FS)
sda3 - Linux swap.

I've backed up my mbr (using dd=...), and intended to backup my /etc/fstab as well, yet my fstab doesn't include any reference to the XP (current) multiple partitions an sda (why?). I'm worried about grub as well.



For reference, here are my current HD structure, fstab, mtab and menu.lst:

--------output of "fdisk -l"  ---------------

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf82ef82e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1110     8916043+   7  HPFS/NTFS
/dev/sda2            1111        8621    60330315    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            8622        8812     1534207+  82  Linux swap / Solaris
/dev/sda4            8813       10011     9630967+   5  Extended
/dev/sda5            8813        9639     6642846    b  W95 FAT32
/dev/sda6            9640       10011     2988058+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000970c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         892     7164958+  83  Linux
/dev/sdb2             893       21034   161790615   83  Linux
/dev/sdb3           21035       22755    13823932+  83  Linux
/dev/sdb4           22756       24321    12578895   83  Linux

----------- copy of my /etc/fstab------------------


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=0a23379c-0335-4bca-8993-204a1607c49b /               reiserfs notail,relatime 0       1
# /dev/sdb2
UUID=57e7f715-35b8-4e97-9ff8-53542390832a /home           reiserfs relatime        0       2
# /dev/sda3
UUID=8f49b6b3-0bdd-4e6e-96d9-de43c5f83b2d none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


---------------end--------------

after I mount all my current sda partitions, the following lines appear at the end of my /etc/mtab:

/dev/sda1 /media/disk fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda6 /media/c\040extended fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sda2 /media/Data fuseblk rw,nosuid,nodev,noatime,allow_other,blksize=4096 0 0
/dev/sdb3 /media/-Images ext3 rw,nosuid,nodev,uhelper=hal,data=ordered 0 0
/dev/sdb4 /media/-Misc ext3 rw,nosuid,nodev,uhelper=hal,data=ordered 0 0

---------------------

And, finally, my /boot/grub/menu.lst looks as follows (for clarity, I've omitted the initial defaults and comments lines):

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-18-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=0a23379c-0335-4bca-8993-204a1607c49b ro quiet splash
initrd          /boot/initrd.img-2.6.24-18-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-18-generic root=UUID=0a23379c-0335-4bca-8993-204a1607c49b ro single
initrd          /boot/initrd.img-2.6.24-18-generic

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=0a23379c-0335-4bca-8993-204a1607c49b ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=0a23379c-0335-4bca-8993-204a1607c49b ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0a23379c-0335-4bca-8993-204a1607c49b ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0a23379c-0335-4bca-8993-204a1607c49b ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
-----------------




What shall I do (detailed instructions if possible) to ensure a smooth PC upgrade?

Thanks a lot up front!


Regards,

Michael Badt

---

### Post by askreet on 2008-06-08
I've backed up my mbr (using dd=...), and intended to backup my /etc/fstab as well, yet my fstab doesn't include any reference to the XP (current) multiple partitions an sda (why?). I'm worried about grub as well.

They don't appear because they're not mounted at boot-time.  I'm not sure what the software is (maybe hotplug, or some newer derivative), but it mounts things like Windows partitions, USB keys, etc. after the fact.

So how are you planning to move the data from the existing disk to the new disk?  Or are you?  Copying your MBR is a great idea, and should work fine.

---

### Post by mibadt on 2008-06-08
AS for transferring my data to the new drive, I've already tar zipped it into my remaining Linux home.

Regards,

Michael Badt

---

