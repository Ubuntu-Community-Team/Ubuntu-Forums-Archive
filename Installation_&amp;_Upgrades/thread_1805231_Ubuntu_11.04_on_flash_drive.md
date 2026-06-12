---
title: "Ubuntu 11.04 on flash drive"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by Jimfox on 2011-07-15
I want to install Ubuntu 11.04 on to an 8GB flash drive. Not create a Live USB. How would I go about doing with? What would the partitions be if i have 6 gigs of RAM?

---

### Post by oldfred on 2011-07-15
I installed to a 16GB flash with 8GB for / (root), no swap ( I have 4GB of RAM and almost never have used swap) and left the other 8GB for data. It is a little slower in loading as both USB and flash are slower than SATA port and hard drive. You do want to make some settings to reduce writes which help speed a little, otherwise it is just like any install to a second drive. You want to use manual install so you get the choice to install grub2's boot loader to the MBR of the flash or else the default is sda (usually the internal drive).

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

---

