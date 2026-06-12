---
title: "Ubuntu 9.10 Installer Fails on Partitioning"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by Lux01 on 2010-02-07
Hi,

Whenever I try to install Ubuntu 9.10 x64 from a Live CD the installer freezes or quits when trying to partition the drive. I tried booting into the Live environment and using GParted but that would only let me make a ReiserFS partition without crashing. With the Reiser partition I tried the installation program again but this time the installer froze when trying to install the files.

My system specs are:
AMD Athlon 64 X2 6000+ (3.0GHz)
4GB RAM
500GB SATA2 HDD
ATI Radeon HD 4770

Currently it also has a second SATA2 HDD with Windows 7 installed but I disconnect this during installations.

Any help would be greatly appreciated. Thanks!

---

### Post by drs305 on 2010-02-07
Gparted should not have had a problem creating the partitions or formatting the drive.

A few options you could try would be:
1. Format the drive to NTFS via a Windows app and then try Gparted again to format it to ext3/4. 
2. Create a Gparted or SystemRescue CD and try to format/partition the drive with one of those. Having a SystemRescue CD or USB thumb drive available can come in handy for a variety of problems.
[http://sourceforge.net/projects/gparted/files/gparted-live-stable/]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/")
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")
3. Of course, you can also check the integrity of the Ubuntu LiveCD or use the Alternate CD but I don't think that is the issue here.
4. If this is a new drive, you might also try the initial formatting from within Windows using whatever partitioning software came with the drive.

---

### Post by sanderj on 2010-02-07
Have you tried the 32-bit version of Ubuntu? If that works neither, it's not specifically a 64-bit problem.

If 32-bit doesn't work, have you tried an older or newer Ubuntu?

---

### Post by Lux01 on 2010-02-09
I used the SystemRescueCD to create partitions on the drive for 9.10 but then the installer failed when copying over to the hard disk.

I tried the Alternative Installer, it again failed on partitioning and failed when copying files to pre-made partitions.

I tried installing Ubuntu 9.04 (64-bit). This installed successfully and updated completely. I ran a dist-upgrade to get 9.10 which finished successfully but then whenever I boot into 9.10 everything stops responding once I reach the desktop.

I think I'll stay with 9.04 and see how my machine handles 10.04 when it's released.

---

### Post by sanderj on 2010-02-09
If 9.04 (and then upgrading to 9.10) works OK, and 9.10 does not, you could indeed use the 9.04 -> 9.10 path, AND report (or first search for) the bug on launchpad.

---

