---
title: "Having &quot;fun&quot; trying to install Ubunt from USB onto degraded RAID, encrypted HDD"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by thezman007 on 2015-09-30
The file system got borked at some point awhile ago and I am trying to reinstall Ubuntu without any RAID shennanigans. It was a motherboard RAID1 (NEVER AGAIN!!!), After chasing what I thought was a hardware issue I realized it was the I/O of the drive(s) themselves. I have been playing this game for several hours at this point. The TL;DR version is this:

The installer wants me to select a device for boot loader installation. However on the HDD where I already removed the /dev/mapper stuff using dmraid it doesn't see any file system even though I formatted it with Gparted while using the LiveUSB. The other (untouched) HDD will only show up after it's mounted, but mounts as /dev/mapper/XXXXXX. I DO NOT want to install it on a dev/mapper scenario. How can I fix this? All data is backed up. so no worries there at least :D 

I just want to install Ubuntu onto sda1, or sda2, or whatever partition is appropriate.

TIA

---

### Post by oldfred on 2015-10-01
Drives retain RAID meta-data. You need to remove that if totally erasing RAID.

 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

