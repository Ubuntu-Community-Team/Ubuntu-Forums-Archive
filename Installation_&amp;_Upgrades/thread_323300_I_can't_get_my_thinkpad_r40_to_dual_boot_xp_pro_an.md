---
title: "I can't get my thinkpad r40 to dual boot xp pro and ubuntu 6.10"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by axio720 on 2006-12-21
i am fairly new to Linux.  I have been trying to make my ibm thinkpad r40 laptop a dual boot system.  I want to be able to boot win xp pro and Ubuntu 6.10.  I have gone through the forums several days in a row now looking for guidance.  I have tried every possible thing that i have found.  I have a fairly small hard drive, 20 GB.  Now i don't need much space for my xp either.  i run two small programs and office.  I have a medium sized music collection that is continuing to grow.  I plan to put that on the fat32 share.  Well despite the low amount of space this configuration is more for the learning than anything.  
I am using a non-IBM version of xp.  i don't want to deal with the backup stuff and service partition.  When I am able to get my hands on a larger hard drive I will probably attempt to ghost or backup and migrate to the larger hard drive.  That is not the issue i am facing now.
It's not a great system but i really just want to start learning.  I would have just Linux and be done with it but my wife doesn't to learn Linux just yet.  She said she would prefer me use it for a few months and kind of know what i am doing before we get rid of windows.  In addition I am not a mac hater or pc hater or anything like that.  I just love computers and want to learn anything i can about them.


My current configure plan is this:
1st partition- NTFS - XP PRO - 10 GB
2nd partition- EXT3 - UBUNTU 6.10 - 5 GB
3rd partition- LINUX SWAP - SWAP - 512 MB
4th partition- FAT32 - SHARE - about 4.5 GB

PROBLEM:
I install xp and it works.  Then my next step is to install Ubuntu and that works.  Then when GRUB boots it show Linux and xp but it wont go into windows. It just keeps coming back to the GRUB menu.  How do i get GRUB  to boot into windows and Linux.  right now i have reinstall several different ways and just have to keep trying over and over.  please someone show me the way.  i am just so frustrated and i am willing to answer all the basic little question to get it to work.  Please help!!!!!

nathan

p.s. i am worried about reformatting to many times and ruining the only hard drive i have right now.

---

### Post by Sef on 2006-12-21
Could you copy and paste the results of this command: 

sudo fdisk -l

---

### Post by axio720 on 2006-12-22
this is what i got

Disk /dev/hda: 20.0 GB, 20003880960 bytes
15 heads, 63 sectors/track, 41344 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         221      104391   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/hda2             222       34153    16032870    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3   *       34171       41344     3389683+   b  W95 FAT32
Partition 3 does not end on cylinder boundary.
/dev/hda5             225       21904    10243768+   7  HPFS/NTFS
/dev/hda6           33083       34153      506016   82  Linux swap / Solaris
/dev/hda7           21914       33082     5277321   83  Linux

Partition table entries are not in disk order

thanks for your help.
nathan

---

### Post by Sef on 2006-12-26
Windows likes to be on the first partition (hda1.)   Also that should be the boot partition.   I do not know how to change it around without reformatting.   It might be possible for you to back it up on to an external hard disk  and then reformat the hard drive and then put on Windows on hda1, but someone else would have to explain how to do that.

---

### Post by axio720 on 2006-12-27
okay I redid the whole hard drive with xp 1st,  linux 2nd, swap on an extended third partition as linux swap,  fat32 share as partition 4.  xp booted perfect after installing fresh.  then after i installed ubuntu grub cones up with 5 options:

Ubuntu, kernel 2.6.17-10-generic
Ubuntu, kernel 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operationg systems:
Microsoft Windows XP Professional

if i select windows it comes right back saying 
Starting up....
grub loading stage2
 then goes back to grub page...

please help me!!! 

this is how i want it.

xp ntfs hda1
linux ext3 hda2
os share fat32 hda4
on extended hda3:
linux swap swap hda5

---

