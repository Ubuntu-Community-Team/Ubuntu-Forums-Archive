---
title: "improper ubuntu removal"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by atu22 on 2010-06-15
I had a computer with the following partitions:
System: 100mb, primary
C: 100gb, primary //windows
F: 600gb, logical //data
G: 50gb, primary //empty, for linux

I think I did something wrong when installing Ubuntu, as manually choosing the G partition didn't work as I got some error, so I let the installer choose its own partition. It chopped off a part of the F partition to create its own and installed Ubuntu there. When I would boot the computer I had the option to choose between Windows and Ubuntu, and both worked. I however wanted to remove Ubuntu so that I could reconfigure/rethink partitions so I formatted the partition with Ubuntu on it, thinking that would work.

Now when I boot the computer (I'm writing this using Ubuntu live-cd), I get something like "can't find partition"  --> Grub rescue prompt

What I want to do is to remove any trace of Ubuntu/Linux from my harddisk so that it boots Windows again.

Any help would be greatly appreciated.

On another forum I read that this command would be useful, so I'm including it:
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3474d207

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102297600    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           12750       91201   630163769+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5           12750       53608   328197372+   7  HPFS/NTFS
/dev/sda6           53609       91201   301961488+   7  HPFS/NTFS

Disk /dev/sdb: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x454c62fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4870    39118243+   7  HPFS/NTFS

---

### Post by lechien73 on 2010-06-15
It seems that formatting the Ubuntu partition has caused problems with your bootloader.

You didn't specify what version of Windows you are using, but if you it to boot the way it used to, then follow the instructions to restore your MBR here:

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by atu22 on 2010-06-15
I use windows 7-64 bit. -- it used to boot automatically, so I thought that with formatting the ubuntu-partition any changes would also be removed.

---

### Post by lechien73 on 2010-06-15
Formatting the Ubuntu partition removed Ubuntu, but not the Grub bootloader. It's like the difference between just deleting an application and actually uninstalling it.

The link I posted will help you restore your previous Windows 7 bootloader. Hope you come back to Ubuntu when you have figured out your partitioning scheme :)

---

### Post by atu22 on 2010-06-15
> **lechien73 said:**
> Formatting the Ubuntu partition removed Ubuntu, but not the Grub bootloader. It's like the difference between just deleting an application and actually uninstalling it.

The link I posted will help you restore your previous Windows 7 bootloader. Hope you come back to Ubuntu when you have figured out your partitioning scheme :)

Yes, in retrospect that seems to make more sense than what I thought. I will try to follow the instructions in that link now, thanks.

---

