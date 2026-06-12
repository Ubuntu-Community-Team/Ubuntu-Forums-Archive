---
title: "[lubuntu] Boot and install on external hard drive"
date: 2015-11-01
forum: Installation &amp; Upgrades
---

### Post by dogdeblack on 2015-11-01
Hello, I need some help on how I would be able to boot my lubuntu .iso on my external hard drive and install on the same.I´ve done this once using slackware but I dont have any idea as to how this would work with lubuntu.I´m running windows on a notebook so any solutions that can be done only trough linux wont be of much help.Should I just create a new partition and install linux on there? Like for example I format the hard drive and create a 10GB FAT/32 partition[out of 500GB] and leave the 490GB without any partitioning and then install lubuntu on that partition?

---

### Post by dogdeblack on 2015-11-01
So what I tried was using the 10GB FAT32 and the 490GB for the lubuntu instalation but I got an error while trying to install:

[Failed to unmount partitions]

The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom
                                                                                                                     |
Please close any applications using these mount points.                          |

Would you like the installer to try to unmount these partitions again?     |
----------------------------------------------------------------------------------------------
How do I proceed?

---

### Post by yancek on 2015-11-01
Leaving unallocated space on the drive is best as you will have to use the installer for Lubuntu anyway to create Linux filesystems.  Windows is not able to do this. 

> Hello, I need some help on how I would be able to boot my lubuntu .iso on my external hard drive and install on the same.

Do you have the iso on your hard drive?  What are you using to try to boot it?  I don't expect a windows bootloader will do it.  This is a simple matter with Grub bootloader installed to boot the Lubuntu iso.

---

### Post by dogdeblack on 2015-11-01
So here´s what I ended up doing I install oracle´s virtual box on windows and used it to open the iso and do lubuntu´s install on the external hard drive way easier.Just hoping that somehow the vm driver´s will work on the notebook XD

---

### Post by dogdeblack on 2015-11-01
So yeah it ended up being easier to install oracle's virtual box and then intall lubuntu on the external hard drive trough it and afterwards boot from the external hard drive

---

