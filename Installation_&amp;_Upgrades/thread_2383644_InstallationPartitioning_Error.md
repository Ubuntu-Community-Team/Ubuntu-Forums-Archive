---
title: "Installation/Partitioning Error"
date: 2018-01-27
forum: Installation &amp; Upgrades
---

### Post by alazuk88 on 2018-01-27
I've been attempting to install Ubuntu on a 1TB External Hard Drive, I've gotten most of it done, but when I try to actually go through with the install I continuously get this message:
> The partition /dev/sdb2 assigned to / start at an offset of 3584 bytes from the minimum alignment for this disk, which may lead to very poor performance.

I've tried following the instructions that happen to follow after that part of the pop-up message. But it never really fixes anything, I've already searched this error on google and got different answers which I'm having trouble understanding. 

One of them did mention doing "sudo fdisk -lu", I did that and here is the output for /dev/sdb:
> [B]Disk /dev/sdb: 931.5 GiB, 1000204885504 bytes, 1953525167 sectors
[/B]Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0x55042c6c

[B]Device     Boot Start        End    Sectors   Size Id Type
[/B]/dev/sdb1        2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT


---

### Post by TheFu on 2018-01-28
It is important that partitions begin on sector boundaries for performance reasons. Most disks are either 512b or 4Kb sector disks today.  Yours is 4096 (4Kb), so the first usable sector should begin at 4096b.  It is usually easiest to reinstall to get that. If you are clicking next, next, next and this is the result, I guess the defaults aren't good.  "Do something else" is necessary at the disk partitioning option.

BTW, you cannot use NTFS for an install.

---

