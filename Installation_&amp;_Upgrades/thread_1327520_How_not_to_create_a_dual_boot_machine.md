---
title: "How not to create a dual boot machine"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by L0tech on 2009-11-15
After installing 9.04 and loving it, I finally decided on a dual boot system to meet my few remaining windows needs.

Problem is, I seem to have done everything I possibly could in the reverse order. 

I have a 1.5 TB drive I'm using for everything. Previously this drive was just used for all my big music/video storage, and windows was on another drive I no longer wish to use. So the challenge has been: muddle my way through while not being able to fully start over with a clean HDD. I guess I should say that I'm completely new to using partitions, as dumb as that sounds.

Step 1: Installed Ubuntu as first OS
Step 2: Use Gparted to break off 200gb for Windows (set to BEFORE existing partitions... d'oh! Partition table destroyed). I also managed to corrupt the Ubuntu install here somehow.
Step 3: Use [Testdisk to rewrite partition table]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").
Step 4: Install XP on sda1.
Step 5: Reinstall Ubuntu. 

During the Ubuntu install, GRUB failed to install. I'm guessing because there is no boot partition, so a startup goes straight to Windows.

[php]Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc0dfc0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26130   209889193+   7  HPFS/NTFS
/dev/sda2           26132      181771  1250178300    7  HPFS/NTFS
/dev/sda3          182098      182401     2441880   83  Linux
/dev/sda4          181772      182097     2618595    5  Extended
/dev/sda5          181772      182075     2441848+  83  Linux
/dev/sda6          182076      182097      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
[/php]sda1 is the XP partition (and flagged as boot), sda2 is mass storage, and hopefully the rest is recognizeable. I tried following [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") to install GRUB, but GRUB does not like seem to want to install on sda1. I thought I might break off a chunk and just create a boot partition, but I'm already at my max of 4 Primary partitions. Does Ubuntu create 2 Primaries? I'm thinking sda3 is a remnant of the old install, and can be deleted. Any other ideas?

Thanks guys.

---

### Post by darkod on 2009-11-15
You do not want to install grub2 on sda1 (the partition) but on sda (the drive, more precisely the MBR of the drive).
That makes a difference, especially grub2 doesn't like being told to install on a partition. Unless the 1 in sda1 was a typo.
If you still need help after trying sda you can also google, plenty of threads about reinstalling grub2 already as well as tutorials.
Not that we don't want you here of course. :)

Just one of them:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
You have it under number 13, Reinstalling Grub2 with LiveCD

---

