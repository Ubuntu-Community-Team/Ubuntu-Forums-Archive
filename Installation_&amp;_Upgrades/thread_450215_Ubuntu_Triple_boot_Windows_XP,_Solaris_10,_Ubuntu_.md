---
title: "Ubuntu Triple boot: Windows XP, Solaris 10, Ubuntu 7.04"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by smshinde on 2007-05-21
Dear All,
Currently my PC(Pentium 4)  is having two OS's. I can boot from either Windows XP SP2 or Solaris 10 11/06 64 Bit.
The boot manager being Grub installed by Solaris 10.
The HDD is of Seagate SATA 80 GB.

Current disk configuration is:
C: Drive NTFS: 12 GB (Primary)
D: Drive FAT32: 20 GB (Logical Drive in extended partition)
E: Drive FAT32: 20 GB (Logical Drive in extended partition)

Solaris partition of 10 GB (Primary)
13 GB Free Space

I want to install Ubuntu 7.04 (32 bit) in this free space of 13 GB.
When I started the installation, while setting up disk configuration when i choose to use the largest free space available it says too many primary partitions are there.
It also gives me suggestion that i will resize my E drive and use 50% of it. I chosen that also but the same error about primary partitions occurs.

As per my knowledge on one hard disk we can have 4 primary partitions or 3 primary partitions and 1 extended partition.
Here i am having only 2 primary partitions then why Ubuntu is giving this error?

Please guide me in setting up triple boot system.

I am thinking that i will set up Ubuntu. It will make it dual boot with Windows using Grub. Then i will make use of menu.lst file of Solaris grub installation which i copied on my flash drive, modify it for 3 OS's and replace it with Ubuntu installation.

Any suggestions about making it triple boot.

Please guide.

Thanks in advance.


-Sameer

---

### Post by Gina on 2007-05-21
When you install Ubuntu 7.04 Feisty Fawn it automatically detects all existing operationg systems inckluding any existing Ubuntu, Windows etc. and makes a multi-boot system.  On boot up you then get a menu from which to choose.  eg. I have multi-boot on this PC containing 2 Feisty systems (one for testing only), a Dapper system and Windows XP.  I can boot into any of them by simply using the keyboard to choose OS with up/down keys and Enter to select.

Feisty also gives the option to import Documents and Settings from detected OS's, inc. Win and other Ubuntus.

---

### Post by smshinde on 2007-05-21
The problem is with primary partitions as mentioned here.
I know how to make it dual boot as i done it previously with Windows XP but while making it triple boot it is giving  problem.
Why the Ubuntu Installation wizard says that there are too many partitions while only 2 primary partitions are there and one more primary partition of Ubuntu can be supported with this disk configuration.

Do revert.

-Sameer

---

### Post by ashijit007 on 2007-05-24
If you mean to do it this way - 
 [http://blogs.sun.com/richb/entry/partitioning_and_boot_information_for](http://blogs.sun.com/richb/entry/partitioning_and_boot_information_for)
I think it will go alright.

---

