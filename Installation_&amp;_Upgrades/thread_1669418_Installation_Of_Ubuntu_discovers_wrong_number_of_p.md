---
title: "Installation Of Ubuntu discovers wrong number of partitions"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by Big Dazed and Confused on 2011-01-17
Hi All , 

I have problem Installing the new Release Ubuntu 10.10 on my PC. 
My plan is for dual boot with win7 x64 .
Problem description : 
I have 500GB HDD (SATA) with 5 partitions on it. 
One of the partitons is RAW and not formatted  . 
Installer shows only 3(sda1,sda2,sda3)  of the partitions and last one is the size of the  3 partitions . 
The HDD discoverd on  diskmgmt.msc as Dynamic disk (is it relevant?) . 
 

Thanks , 
Roy

---

### Post by Quackers on 2011-01-17
Yes, dynamic disks are extremely relevant. It seems you may have tried to create a 5th primary partition, when only 4 are allowed. In these circumstances Windows 7 will convert all primary partitions to dynamic disks. This is not a problem for Windows 7, but it is a problem for any other operating system. The hard drive will not be properly recognised and no further installation can take place.
It is possible to convert the partitions back to primary, but it is a long and complicated road, as I understand it. It may be better to re-install Windows and start again.
But this time don't try to create mor than 4 primary partitions (including an extended partition).

---

### Post by Big Dazed and Confused on 2011-01-20
Writing now from Ubuntu  :) , Dynamic disk  was the problem . 
Solution was much easier : I have used TestDisk to convert disk 
to Basic and then Installed Ubuntu 10.10. 
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by Big Dazed and Confused on 2011-01-20
Writing now from Ubuntu  :) , Dynamic disk  was the problem . 
Solution was much easier : I have used TestDisk to convert disk 
to Basic and then Installed Ubuntu 10.10. 
[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by oldfred on 2011-01-20
Did testdisk let you convert SFS dynamic to basic? We have been looking for way. Did you have any issues. Do you know the exact procedure you followed?

---

### Post by Quackers on 2011-01-20
Well that's news :-)
It would be nice to know what you did exactly :-)

---

### Post by srs5694 on 2011-01-20
Actually, TestDisk converting SFS volumes to regular partitions makes sense, but with a big huge flaming caveat (see below). TestDisk works by scanning the disk for filesystem "signatures." So long as the SFS volumes aren't encrypted, those signatures will be present, and TestDisk will be able to find the filesystems and create partitions that contain them to replace the SFS partition....

HOWEVER (here's the big flaming caveat), my understanding is that SFS/dynamic disks works like Linux's LVM. If so, the volumes contained in the SFS partition might not be contiguous. If so, TestDisk might create a partition that holds *part of* the filesystem that TestDisk first detected, but then switches to something else. Without knowing more about how the volumes in any given SFS partition are laid out, it's impossible to say if this would actually be a problem for any specific system. Personally, I wouldn't risk it unless I knew for a fact that any volume(s) I wanted to recover consisted of a contiguous set of sectors.

OTOH, it's possible that TestDisk has SFS-reading capabilities I don't know about, in which case it might be able to do this more safely....

---

### Post by freshmeat20 on 2011-01-24
Sweet! I  can read my sfs files with testdisk but dont know how to get to booting it again?
It has a selection to change type to NTFS but reverts after console closes?

---

