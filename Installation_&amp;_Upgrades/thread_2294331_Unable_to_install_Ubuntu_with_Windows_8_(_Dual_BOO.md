---
title: "Unable to install Ubuntu with Windows 8 ( Dual BOOT)"
date: 2015-09-10
forum: Installation &amp; Upgrades
---

### Post by ignacio5 on 2015-09-10
I want to install Ubuntu alongside Windows 8 . 

I've disables de FastStart , The Secure Boot AND created a partition with windows to install ubuntu on it.
 The thing is that when i star the PC with the liveUSB. It recognizes it. I press try it, everything perfect. Once I try to install Ubuntu the Installation Type option never comes up, and when i have to choose a partition, there is none to choose. So i started a little research and i don't have  a solution.

I went ahead and used the code ```
$ sudo fdisk -l 
```

And it showed me this


[INDENT]```
WARNING: GPT( GUID Partition Table) detected on '/dev/sda'! the util fdisk doesn't support GPT. Use GNU Parted.

Disk/dev/sda : 1002 GB , 1000204886016 bytes
256 heads, 63 sector/tracks , 121126 cylinders , total 1953525168 sectors
Units = sectors of 1*512 = 512 bytes.
Sector size ( logicla/physical) : 512 bytes/4096 bytes
I/O sizw ( minimum/optimal) : 4096 / 4096 bytes
Disk identifier: 0xc97773180

Device Boot    Start     End                   Blocks        Id     System
/dev/sda1           1    4294967295    2147483647+   ee     GPT
Partition 1 Does not start on physical sector boundary

WARNING: GPT( GUID Partition Table) detected on '/dev/sdb'! the util fdisk doesn't support GPT. Use GNU Parted.


Disk/dev/sdb : 24 GB , 24015495168 bytes
256 heads, 63 sector/tracks , 6794 cylinders , total 7826688 sectors
Units = sectors of 1*512 = 512 bytes.
Sector size ( logicla/physical) : 512/512 bytes
I/O size ( minimum/optimal) : 512/512 bytes
Disk identifier: 0xc3072e18


Device Boot    Start     End                   Blocks        Id     System
/dev/sdb1           1    4294967295    2147483647+   ee     GPT


Disk/dev/sdc : 4007 MB , 4007264256 bytes
128 heads, 9 sector/tracks , 6794 cylinders , total 7826688 sectors
Units = sectors of 1*512 = 512 bytes.
Sector size ( logicla/physical) : 512/512 bytes
I/O size ( minimum/optimal) : 512/512 bytes
Disk identifier: 0xc3072e18


Device     Boot    Start     End                   Blocks        Id     System
/dev/sdc1  *         56       7826687           3913316      c        W95 FAT32 (CBA)
```



[/INDENT]
According to what i understand the first disk is the main hard drive ( 1 TB). the second disk is the recovery for windows, and the last one is the pendrive from which I am booting ubuntu. 

The partition I made is 80 GB and it's recognized by windows. 

WHY can't I install Ubuntu.

I'm running an HP envy 15. 

Thanks!!!

---

### Post by yancek on 2015-09-10
As you can see in the first line of the output you posted, fdisk doesn't support GPT.  Your computer is using GPT partitioning so use the suggested GParted which is on the install disk.  Should be an icon in the panel at the left otherwise open it from a terminal and post the image here.  Also, the fdisk output shows three physical drives, 1TG, 24GB and the 4GB flash drive.  You might be better off shrinking the windows system from windows and just leaving 80GB of unallocated space for Ubuntu.  You will have to format during the install anyway because windows is not capable of doing that.

---

### Post by ignacio5 on 2015-09-10
The 80 GB forma ubuntu aré in an allocated disk. I Will try to do the partioning differently.


thanks!

---

### Post by Mark Phelps on 2015-09-11
> AND created a partition with windows to install ubuntu on it.

Windows can NOT create Linux filesystem partitions -- and THAT is what you need in order to install Ubuntu.  You need to remove the partition you created with Windows. 

When you boot from the Ubuntu install media, choose the Something Else option to create a Linux filesystem partition.

---

