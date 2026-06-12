---
title: "Converting swap space to ext2 or ext3"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by ubunssk on 2011-08-20
Hi 
I want to convert my swap space 8GB to usable format
Here is the output of sudo fdisk -l command

$sudo fdisk -l


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26af26ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2295    18434556    7  HPFS/NTFS
/dev/sda2            2296        9728    59705572+   f  W95 Ext'd (LBA)
/dev/sda5            2296        4590    18434556    7  HPFS/NTFS
/dev/sda6            6886        9728    22836366    7  HPFS/NTFS
/dev/sda7            4591        5669     8667036   83  Linux
/dev/sda8            5670        6885     9767488+  82  Linux swap / Solaris

Partition table entries are not in disk order

I have dual boot ubuntu and winxp.

---

### Post by Basher101 on 2011-08-20
simply deleting your swap in Gparted and creating an ext4 filesystem from the unallocated space should do the trick (swap is brown/orange in Gparted)

---

### Post by sanderd17 on 2011-08-20
Boot up a live CD/USB, open gparted, delete the swap partition and enlarge SDA7 (you may need to unmount the swap first by right-clicking on it).

---

### Post by oldfred on 2011-08-20
Best to keep some swap, but if you have at least 4GB of RAM and do not hibernate you should be ok. I normally suggest 2GB of swap.

You will have to edit out the swap entry in your fstab.

You could just add swap as a file.

HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

