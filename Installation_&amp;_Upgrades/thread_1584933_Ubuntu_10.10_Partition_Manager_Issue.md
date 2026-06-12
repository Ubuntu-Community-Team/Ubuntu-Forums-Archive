---
title: "Ubuntu 10.10 Partition Manager Issue"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by Qboy61 on 2010-09-29
I am trying to install Maverick Meerkat on a machine with Windows 7 in dual boot. Why have they removed the selection for "Install in the largest contiguous empty space on the hard disk" in Ubuntu 10.10? Maybe I'm just not finding it. I have installed 10.10 with the default selection to "install side by side" on several machines and it always adjusts the Windows partition. I used to select the 3rd option down in 10.04 and before which was to install to the largest contiguous emply space and it had no effect on my Windows partitions. 
 
:confused: :(

---

### Post by efflandt on 2010-09-30
There is another forum for 10.10 until it is released [http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

Frankly I never trust automatic partitioning from years ago.  Even when I told 64-bit WinXP beta to use an existing partition, it changed my partition table geometry (heads/cylinders) so it could not boot itself or XP Home.  I managed to fix it using fdisk from a Linux live CD with a bit of trial and error, since the only thing I had to go on was memory in my head after earlier using ntfsresize.  No data lost.  When I was then installing a version of SuSE from that time I caught it (from numbers it quoted on the screen) before it was about to likewise change disk geometry.  So I forced it to use the partition I set up for it as is without touching my partition table.

So far I only installed 64-bit 10.10 beta to a USB hard drive.  I partitioned it first with gparted from live CD before installing.  A pleasant surprise is that when you put / on a USB drive, it automatically defaults to putting grub on the external drive.  That should minimize accidentally putting grub on a main hard drive when installing to an external drive.

---

