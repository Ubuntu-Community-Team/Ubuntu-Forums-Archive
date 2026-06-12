---
title: "Cant install Ubuntu"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by rjt11890 on 2009-11-21
Im trying to install Ubuntu Netbook Remix on my new Asus Eee PC 1008ha. It came with Windows 7 and im trying to dual boot both OSs. On my hard drive there are five partitions:

*Windows 7 (loader) (/dev/sda1) NTFS 100GB
*/dev/sda2 NTFS 77.9 GB, for windows 7 data
*Free Space 110.2 GB
*Windows Vista (loader) (/dev/sda3) Fat32 10.0 GB (hidden)
*Unknown (/dev/sda4) 15.8 MB

When I try to make my "free space" into ext4, for ubuntu, it say that there are already four primary partitions and that I cant make anymore. I want to keep Windows 7 to dual boot it with ubuntu. I dont know why I have a partition with windows vista on my hard drive or if it has anything to do with windows 7. Also I have no clue what the unknown 15.8 MB are for either. Should I delete the 2 partitions?

---

### Post by rjt11890 on 2009-11-22
So i found out that the 16 MB partition that says "windows vista (loader)" on it is actually an "EFI System Partition". Do i need this? What does it do? What happens if i delete it?

---

### Post by ahmet1916 on 2009-11-22
Hey there

I do not know the Eeepc 1008ha well but you may not want to lose the 10GB Vista partition couse it may be the "recovery partition" for your Eeepc. If so you may also need the 16MB Vista boot partition to recover your Eeepc by booting from this partition.

You may create a partition table on the free space of your disk and you should create an "extended" partition (not primary) for "/" and a swap area to proper use of Ubuntu. We users are limited to have four primary partitions on the partition table and you have the four already. You may want to give a try to create extended partitions on your free space.

Hopefuly it works for you as well.

---

### Post by cliffbreaker on 2009-11-22
First of all reinstall Windows 7. Seems it is a pre-release version, the loader must be not Vista loader, but Windows 7 loader - what you've got here is only a bunch of files called windows 7

---

### Post by rjt11890 on 2009-11-22
Im trying to make the "free space" and extended partition but when i highlight it, it wont give me the option to do anything except for "revert" and "new". When i click on "new" i get the message again telling me that i cant make more than 4 primary partitions. How else can i make the "free space" and extended partition?

---

