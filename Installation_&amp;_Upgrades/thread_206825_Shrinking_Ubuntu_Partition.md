---
title: "Shrinking Ubuntu Partition"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by DonMateo on 2006-06-30
Hello, I'm very new to Linux and dual booting, and I was wondering how I can dual boot Windows XP and Ubuntu in the situation I'm in. On my 60gb drive I have just a Linux partition,  and I know I need to make a partition for Windows. Is it possible to shrink my Linux partition to make room for a new Windows one without messing up the Linux partition? Or do I have to start over and delete my Linux partition? Thanks.

---

### Post by BitTorrentBuddha on 2006-06-30
You can safely shrink the partition. Use the live CD to run gparted or use an equivalent (i.e. partition magic.) Make the Linux (ext3) partition as small as you need, then make a new partition for windows (NTFS for just windows or FAT32 if you want to access files from Linux as well.)

---

### Post by bukwirm on 2006-06-30
Yes, the gparted utility (inculded on the LiveCD) can be used to resize partitions. However, installing Windows will erase GRUB, so you might want to check out this link: [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=restoring+grub]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=restoring+grub")

---

### Post by user1397 on 2006-06-30
[quote=DonMateo]Hello, I'm very new to Linux and dual booting, and I was wondering how I can dual boot Windows XP and Ubuntu in the situation I'm in. On my 60gb drive I have just a Linux partition,  and I know I need to make a partition for Windows. Is it possible to shrink my Linux partition to make room for a new Windows one without messing up the Linux partition? Or do I have to start over and delete my Linux partition? Thanks.[/quote]yes you can shrink your linux partition, and create unallocated space (free space) for the new windows installation.  try using the program **gparted**, which is included in the ubuntu 6.06 desktop cd.  i don't know about installing windows *after* ubuntu though, since windows would overwrite GRUB.  It would be easiest to install windows, and then install ubuntu.  If you followed that order, the guide in my signature would prove best for detailed steps on how to do that. (the one called "dualbooting ubuntu and xp"

---

