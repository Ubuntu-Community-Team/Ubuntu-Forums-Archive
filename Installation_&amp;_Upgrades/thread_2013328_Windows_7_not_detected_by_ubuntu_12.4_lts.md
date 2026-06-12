---
title: "Windows 7 not detected by ubuntu 12.4 lts"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by mineturtle on 2012-06-30
recently, i decided to dual boot my Hp g7-1270sd notebook (Windows 7 Home premium 64 bit) with ubuntu 12.4. When i opened the installer of ubuntu, it said that there was no operating system installed. I had only 2 options: Erase disk and install ubuntu, and something else. 

When i hit " something else" It displayed every partition as free space, but disk utility detects the partitions. and when i enter in the terminal "sudo fdisk -l" it detects my partitions too.

i also repaired some startup problems with my win 7 recovery cd, but it still doesnt work. 

Ubuntu 11.10 has the same problem. :-(

anyone knows how i can install ubuntu on my notebook?

thanks in advance,

Mineturtle

---

### Post by darkod on 2012-06-30
Can you post the fdisk results?

---

### Post by mineturtle on 2012-07-01
okay, this is the result from the "sudo fdisk -l" command:

isk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa0377689

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2   *      409600   915327346   457458873+   7  HPFS/NTFS/exFAT
/dev/sda3       915329024   976769023    30720000    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 3999 MB, 3999268864 bytes
82 heads, 18 sectors/track, 5292 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x378598b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7811071     3901504    c  W95 FAT32 (LBA)


I have 3 partitions:

the first one is the system partition
the second is my windows 7 partition
the third one is the partition where i want to install Ubuntu

My hdd is 500 gb in total

I hope you guys can do something with this,

mineturtle

---

### Post by darkod on 2012-07-01
If you plan to install on sda3, it's best to delete that partition and leave the space as unallocated. sda3 is NTFS partition created in windows and ubuntu doesn't install on ntfs.

But even with that, it should still detect win7.

Try deleting sda3 and start the install process again to see if that changes anything.

---

### Post by mineturtle on 2012-07-04
Unfortunately,that didnt help. But i have got some extra information.

I booted into my gparted live cd, and gparted opened a window which said that my drive contained some gpt signatures, and it asked me if it was a gpt drive. I first choosed that it wasnt a gpt drive. It gave me exactly the same result as the installer, 500 gb of unllocated space.

Could the gparted notification have something to do with that i am not able to install Ubuntu?

---

### Post by darkod on 2012-07-04
Yes, it could. The disk was with a gpt table earlier and if you converted it to msdos with windows, it doesn't delete the backup gpt table. So linux tools are confused whether the disk is msdos or gpt.

Usually fixparts solves this problem but now it depends if Gparted tried to do anything after that message.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by mineturtle on 2012-07-04
Yes, it worked! My hdd was gpt, but i restored it to mbr. I Used fixpart and i installed Ubuntu, so my problem is solved.

Thank you Darkod!

---

