---
title: "Any issues using common /home for Ubuntu and Lubuntu?"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by efflandt on 2012-07-19
I was just wondering if there would be any potential issues using a common /home partition for both Ubuntu and Lubuntu (64-bit 12.04).

It would be for comparing them to see if there really is any speed difference for Lubuntu on a 1 GHz 2 core tablet PC  w/2 GB RAM (AMD C-50 w/ATI HD video) 1280x800.  It currently has Win7 Pro on its 32 GB SSD and 64-bit 11.10 on 16 GB SD card.  But I just picked up a 32 GB SD that I could use to compare both Ubuntu and Lubuntu.

I'll probably do that this weekend and report back if I do run into any issues.  64-bit 12.04 live iso boots fine on it from USB stick (not real quickly of course).

---

### Post by idoitprone on 2012-07-19
> **efflandt said:**
> I was just wondering if there would be any potential issues using a common /home partition for both Ubuntu and Lubuntu (64-bit 12.04).

It would be for comparing them to see if there really is any speed difference for Lubuntu on a 1 GHz 2 core tablet PC  w/2 GB RAM (AMD C-50 w/ATI HD video) 1280x800.  It currently has Win7 Pro on its 32 GB SSD and 64-bit 11.10 on 16 GB SD card.  But I just picked up a 32 GB SD that I could use to compare both Ubuntu and Lubuntu.

I'll probably do that this weekend and report back if I do run into any issues.  64-bit 12.04 live iso boots fine on it from USB stick (not real quickly of course).

If it is two different installs and you are using the same user, then it maybe a problem. However, it might be ok to use the same home if you use two different users, so there wont be any configuration incompatiblity

---

### Post by oldfred on 2012-07-19
+1 on idoitprone comments.

I prefer to keep /home in my root and on the same drive as my install. But I have data in separate partitions on multiple drives. And each drive has at least one fully bootable operating system. So when one drive fails, hopefully I have data on other drives as backups, but can fully boot another drive.

So I split /home into the small amount of mostly hidden files and folders that are user related to configuring system and everything else that is just data. But move all standard data and some larger hidden data folders like Firefox & Thunderbird profiles into data partitions. Each data partition is mounted in every install. 

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by efflandt on 2012-07-23
I split the 32 GB SD into 3 partitions about 10 GB each with 1 for home.  Installed Lubuntu first on sdb1 with grub2 in MBR.  I installed Ubuntu to sdb3 without grub.  Everything seems to work so far with a common /home.

I was starting to like Lubuntu until I discovered it has no sound (or volume control) and no current specific docs to get that working.  All the same sound modules are loaded as for Ubuntu where sound works.  But for some reason the PCM device that shows up in alsamixer in Ubuntu is missing from Lubuntu.  But that will be subject for a different forum.

---

