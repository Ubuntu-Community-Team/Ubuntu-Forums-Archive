---
title: "RocketRAID 1640 install"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Neezer on 2009-12-21
Hi,

I'm trying to install ubuntu server with a RAID1 array for my media. I am going through the install process, and when I get to the detecting disks part, it says I don't have any partitionable disks, and asks for a driver name...

I have a rocketraid 1640 card with both of my 1.5 TB drives plugged into it. I went into the bios for the card and created the RAID1 array so I thought I was home free....

Any help?

---

### Post by punkybouy on 2009-12-21
You would still need some kind of Linux driver for the Rocket Raid chip or controller. Sometimes the distribution has them and if it finds the controller it will load the driver.  In your case it did not so it does not see the drives.
Have you tried the motherboard or manufacturer's website?

---

### Post by Neezer on 2009-12-21
well,

I am not sure which version of ubuntu server I was using...9.04, or 9.10, but I tried with 9.10 desktop and booted into the live CD. then clicked on the install button, and it is going ahead smoothly. I got worried when it stayed at 5% complete for partitioning my hard disks, but I guess 1.5 TB drives take a while to partition and format.....

I'll post another update upon completion, but everything is looking good now.

In my BIOS the RAID array was showing up as 1 disk, and in the partition part of the the install I was also only seeing one RAID drive...so it should be good as far as I know...

Is there a way to check and make sure that I am indeed using RAID1 after the install process is complete?

---

### Post by gilson585 on 2009-12-22
It should have the hdd's and the array listed in */dev/mapper*. In a terminal just type **ls /dev/mapper** it will list them. Also **dmraid -r** will give more output. Just a few notes here for reference, *fdsik* doesn't currently work right with *dmraid* use *gparted* instead, if you ever install Ubuntu onto a raid array it will not boot, instructions to resolve this are here [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) basicly you remove Grub2 and revert to Grub1.

---

