---
title: "Trying to get full installation from wubi"
date: 2013-10-12
forum: Installation &amp; Upgrades
---

### Post by Ajay_Tripathi on 2013-10-12
I'm trying to use the migrate wubi script, but the problem is that my ubuntu doesn't seem to be installed like it should be?

I run the command:

sudo bash wubi-move.sh /dev/sda5 /dev/sda6

and get the output:

wubi-move.sh:  Validating migration source...
wubi-move.sh:  Source for migration validated successfully:
wubi-move.sh:    Wubi host partition: /dev/sda2
wubi-move.sh:    Size of install: 26960264 K
wubi-move.sh:    Size of /boot: 105056 K
wubi-move.sh:    Size of /usr: 12542664 K
wubi-move.sh:    Size of /home: 10803156 K
wubi-move.sh:  Validating migration target(s)...
wubi-move.sh:  /dev/sda5 is not a valid partition.
wubi-move.sh:  partition /dev/sda5 must be type 83 - Linux.
wubi-move.sh:  swapdevice (/dev/sda6) is not a valid partition.
wubi-move.sh:  Validation of target(s) failed

When I run sudo fdisk -l, I see that I don't have any dev/sda5 or sda6 partitions or anything.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xaf43ec48


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2459647     1228800    7  HPFS/NTFS/exFAT
/dev/sda2         2459648   603635711   300588032    7  HPFS/NTFS/exFAT
/dev/sda3       603635712   625140399    10752344    7  HPFS/NTFS/exFAT




Here's what Gparted tells me things look like:

[IMG]http://i.imgur.com/lMqrtAN.png[/IMG]


So...what do I do? T~T. How can I migrate wubi to a real partition if I don't have dev/sda5 or anything?

Thanks!

---

### Post by TheFu on 2013-10-13
a) I've never used wubi or that script.
b) from the errors and your image looks to me like you need to 
1. reduce the size of sda2 by 50% or more. Looks like there is space for that - use Windows to do this.
2. create an extended partition in the free space - probably named sda4. This is just a container for other "logical" partitions.
3. inside the new extended part, create at least 2 more - 1 for / (root) and another for swap 1x the RAM or 2G, whatever is larger.
4. format the new partition as ext4 and mark the other as linux-swap.
Whatever the new partition names are (could be anything from sda5 - sda20), use those in the wubi migration command.  sda5 and sda6 are likely, but not guaranteed. They should be sequentially numbered.

If you don't understand partitions - read up in the wikipedia article.  primary, extended and logical are the key types on MSDOS partitioned disks. You want Linux to be inside Logical partitions for both the main OS and swap.

---

