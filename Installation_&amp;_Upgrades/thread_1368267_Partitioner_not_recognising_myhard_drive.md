---
title: "Partitioner not recognising myhard drive"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by venkat91 on 2009-12-30
hi

while I try to install  ubuntu the step 4 (partitioner) is not recognising my hard drive at all my hard drive has 3 partitions 
c: 25 gb ( XP os) NTFS
d: 25 GB FAT32
E: 30 GBFAT32
please help me to install ubuntu

---

### Post by ajgreeny on 2009-12-30
From the live CD run gparted and see if it sees the disk, and also run ```
sudo fdisk -l
```(that's a lower case L at the end), in terminal and report the output of that command.

---

### Post by pe1800 on 2009-12-30
I have the same problem, unable to install Ubuntu 9.10 because of problems with GParted not recognizing partitions.

GParted recognizes the first drive as dedicated to WinXP but it dismisses the second hard drive, where I want to install Ubuntu, simply as 80GB Unallocated. It reacted the same before the other distro was installed. No matter what I try, running, as someone suggested, CHKDSK on the Windows partitions, mounting the drives, with two Windows partitions or with one on the second hard drive. GParted will not recognize the partitions on the sdb drive.

From Ubuntu Live, fdisk,the File Manager as well as the Palimpset disk utility have no problem recognizing the partitions. 

Perhaps, I should use fdisk to prepare the sdb drive for Ubuntu....tricky business, better study the man page first........how do I get from the graphical installer to a command prompt?

Thank you for your help and happy New Year!

P.S. Mr. Venkat, do I know you? Where you a manager at Eaton Bay in Toronto? I am Paul Vet. 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe003e003

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2497    20057121    7  HPFS/NTFS
omitting empty partition (5)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x58d7e70e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16      155061    78142711+   f  W95 Ext'd (LBA)
/dev/sdb2           21915       42235    10241437+   7  HPFS/NTFS
/dev/sdb5           42236       67224    12594424+  83  Linux
/dev/sdb6           67225       75350     4095472+  82  Linux swap / Solaris
/dev/sdb7           75351      155061    40174312+  83  Linux
ubuntu@ubuntu:~$

---

### Post by venkat91 on 2009-12-31
Mr.[ajgreeny]("http://ubuntuforums.org/member.php?u=27747") :

i tried it before hand 
there is no out put to display in both gparted option and typing the code in terminal.
but yesterday i tried to put the live cd with my external hard drive of 500gb
but the partitioner recoginises it but not my hard drive where i want to install it.

---

