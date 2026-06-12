---
title: "Recovery of partition"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by untulis on 2012-07-23
I scanned the Forum but I did not see anything that talks to the issue of reinstalling a Ubuntu partition using Wubi.

I used Wubi to install a partition on a Windows 7 system under.  It worked great until my disk crashed. I had ROS installed on the partition and some other code. The data was recovered into an ubuntu directory in a temporary directory.  Under the temporary directory is ubuntu>disks>root.disk which is the size of the partition that I asked Wubi to create. What do I need to do to be able to boot into Windows or into Ubuntu?

If I get it reinstalled, what is the best way to back up the partition. I tried doing a copy of the root.disk file but it was too large to copy onto a USB drive which had plenty of space for the file.

Thanks

Chuck

---

### Post by oldfred on 2012-07-23
Welcome to the forums.

I do not really know wubi but saved some info that may help.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can just reinstall wubi in Windows can replace the new root.disk with your old one if old one still works ok.

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

Read wubi from Windows:
[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

---

