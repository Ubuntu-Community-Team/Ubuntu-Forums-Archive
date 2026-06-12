---
title: "Issues with cloning system disk-help pls"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by three_jeeps on 2010-10-20
Background: I want to make an image copy of my server disk.  I removed the system disk in my server (Ubuntu server 8.04 LTS, 30 GB disk), put it into a USB enclosure, attached it to my Debian 5.0 box and attached another USB disk (40GB). Partitioned and formatted the 40 GB with ext3 file system using gparted.  Ran dd and got an I/O error when copying, read error on the source disk. No clue why. (repeated and got same error)

New approach:
Keep the server disk in the server machine, attach the 40 GB USB disk and run dd.  Several questions using this approach:
1) Good idea to run fsck on the server disk?  If I do, do I need to umount anything?

2) When the server is booted, it runs an number of apps (apache, mysql, postfix, etc.) Is there a way to boot the server and have it come up in 'single user' mode without all the various servers running?  I presume the server should be as 'quiet' as possible before cloning.

3) The 30 GB server disk is the only disk in the server.  Do I need to umount the server disk before I run dd?

4) am I overlooking anything? My approach would be to insert the 40GB USB disk in the server, boot the server, fdisk to make sure of the disk devices, then run dd to copy.  

Thanks for your suggestions.
-John

---

