---
title: "GRUB fatal error during server install"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by sw20 on 2011-07-17
Hello all.
 
I am at a bit of a loss here. I have previously installed Ubuntu Server 9.04 and Server 10.04 without a problem.
 
However, after changing my storage from 3x 1Tb HDD's to 4x 2Tb HDD's, I have been unsuccessful in completing a fresh install of Ubuntu Server 11.04 (64bit).
 
Installation fails when trying to install Grub2 to the MBR. Any attempt to install it on any partition fails (ie /dev/sda or /dev/md0)
 
My assumption is that my error may be occurring due to my partition structure.
 
Initially I created a 60Gb RAID 5, with LVM to be used as Swap... And the remainder as 5.9Tb RAID 5 with LVM to be used as EXT4 with root as the mount point.
 
I have also tried Swap without LVM to no avail (ie RAID 5 only)
 
To rule out issues with the media... I have tried previous install discs for 10.04 & 10.10.
 
Naturally... I have googled the hell out of this problem, and not found a solution.
 
My previous installs with the 3x 1Tb HDD's were also configured as RAID 5 with LVM, and as mentioned before, there were no installation problems.
 
I guess my question is... Does Grub2 or Grub for that matter work on RAID 5 and/or LVM? Is this a problem because I now have 4 HDD's as opposed to 3??
 
 
Any help would be appreciated. Thank you.

---

### Post by Salnayil on 2011-07-22
sw20,

I just ran in to the same issue. I did notice that i had an error earlier in the installation about the RAID so I started over. I received the same error again after selecting the raid about the installer not being able to write to /dev/mapper. This time I hit got back instead and then it was able to find it. I wonder if it is trying to write before it completely loads everything. Either way, after that I was able to complete the installation.

Hopefully that puts you on the correct path.


Thanks
Salnayil

---

