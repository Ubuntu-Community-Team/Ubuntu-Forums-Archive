---
title: "Linux Beginner, Trying to install Ubuntu 13.04 on RAID0, GRUB Failure"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by pingpongitore on 2013-08-28
Hello All, I hope someone can break this down for me as I'm a completely newbie when it comes to anything remotely advanced in Linux. I've booted to my usb drive that holds the LiveCD environment for Ubuntu 13.04 and when I install it to my desktop that has a RAID0 with 4 SSDs, everything seems to go fine then I get a GRUB error when it tries to install the bootloader.

I've tried installing the bootloader using the GUI to every available drive and it gives the same GRUB install error. 

One other thing I tried to do based on googling the issue was to create a smaller RAID for the bootloader and using the remaining space to create the OS RAID.

---

### Post by tgalati4 on 2013-08-28
GRUB likes to be loaded to a single partition on a disk drive.  I don't think you can load it directly to a RAID pool.  

RAID0 is normally used to improve speed by striping data across several slower drives.  It reduces reliability (by 4 times with 4 drives) so it needs to be used with caution.  SSD's are normally pretty fast.  Why would you use RAID0 with SSD's?

---

### Post by pingpongitore on 2013-08-28
I have 4 SSDs in a RAID 0 configuration mainly because of the speed benefit. I got these at a severely discounted rate for a work project that fell through and figured I'd put them to use. All of my data is on an external USB3 RAID5 box that I backup to "the cloud"

Redundancy isn't my concern with the RAID 0 configuration. The performance from 1 SSD, to 4 in RAID 0 is astonishing. Not to mention it is beneficial to have the size of all 4 combined as well. 

I guess the bit I'm not understanding is what you mean by GRUB likes to be loaded to a single partition on a disk drive. Are you saying I would need to have a drive just for the bootloader?

---

