---
title: "Did I lost all my windows files?"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by garbaty on 2013-01-31
Hi. I decided to switch from windows 7 to ubuntu 12.10. I had windows 7 on partition c: and other files (photos, music, animal porn etc.) on partition d:. During intallation i chose c: partition for linux and checked box to encrypt drive. Now on ubuntu i can't mount d: partition. It seems that partition doesn't exist. What to do? Did i lost all my windows files?

---

### Post by furything on 2013-01-31
>  During intallation i chose c: partition for linux and checked box to encrypt drive 
Hopefully you just installed to c: and not whole drive.

Try loading the disk utility to see what partitions it thinks are on the hard drive?

---

### Post by Warren Hill on 2013-01-31
In a terminal enter

```
sudo fdisk -l; mount
```Post the output.  This will tell us if it is still there and if it is we can tell you how to access it

Edit:

You can get a terminal by pressing CTRL+ALT+T

---

### Post by garbaty on 2013-01-31
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2484

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   83  Linux

Disk /dev/mapper/sda5_crypt: 119.8 GB, 119774642176 bytes
255 heads, 63 sectors/track, 14561 cylinders, total 233934848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-root: 116.6 GB, 116551319552 bytes
255 heads, 63 sectors/track, 14169 cylinders, total 227639296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0593f7a2

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
user@user-N-A:~$ ^C
user@user-N-A:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2484

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   234440703   116969473    5  Extended
/dev/sda5          501760   234440703   116969472   83  Linux

Disk /dev/mapper/sda5_crypt: 119.8 GB, 119774642176 bytes
255 heads, 63 sectors/track, 14561 cylinders, total 233934848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-root: 116.6 GB, 116551319552 bytes
255 heads, 63 sectors/track, 14169 cylinders, total 227639296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/mapper/cryptswap1: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders, total 6291456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0593f7a2

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

```

---

### Post by Mark Phelps on 2013-01-31
Why on earth would you choose encryption on what is probably your very first Linux installation?  That makes recovery difficult if not impossible.

The previous windows filesystems are GONE.

If you can decrypt the filesystems, and you can remove this drive and hook it up to a Windows PC, there are Windows data recovery apps that may be able to find the files -- since they search for file name blocks and do not use the partition information to do so.

If you're interested in doing that, go to Runtime Sofware, download and install their RecoverMyFiles product.  You can run the trial version to at least see what it can find.  You have to purchase it to do the actual data recovery.

---

### Post by garbaty on 2013-01-31
Thank for reply. Don't know, for safety? It's not my first Linux installation- 3rd or 4th ;). How can I decrypt the filesystems?

---

