---
title: "Overwrite XP with Ubuntu in existing Ubuntu-XP dual boot"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by Nargren on 2011-10-24
Hey everyone,

I would like to ask for some help if possible.

The situation is the following:
I have Ubuntu and windows XP in dual-boot alongside each other. The hard drive is 80 Gb and since im not using XP any more I would like Ubuntu to "take over" its place. Aka I would like Ubuntu operating system to be extended over the windows partition with its file system and everything (1 partition only)
Is this possible in a relatively simple way or shall I just save my data and reinstall the whole system?

Details:
Windows XP - NTFS
Ubuntu 11.04, Ext3

Thanks!

---

### Post by oldfred on 2011-10-24
Welcome to the forums.

Yes and no.

You can just delete the NTFS partition after backing up any data from it you may want to keep. Then move the Ubuntu partition left into the unallocated space. Moves are a bit more dangerous as any power failure or other problem can corrupt the entire system, so good backups are highly recommended.

But instead of moving the / (root ) partition you could move /home into it or just use it as a new data partition and store some or all of your data from /home in that partition.

For new users I usually suggest the separate /home. But it is a bit more work to move /home to a new partition. More advanced is a separate /data as that has no system or user settings just your data.

Three essentially the same using different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Partitioning basics with some info on /data older but still relavent
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Nargren on 2011-10-24
Thank you for your quick answer!

I was just wondering if this can be done securely and fast, but as there is not much important data on the drive I think I'll get along fine just by formatting the whole drive and reinstall a fresh copy of Ubuntu.

I am looking at the Tutorials and Tips, but I think it will be faster if I just reformat everything and make a uniform file system, I'll add some more swap memory as well.

Thanks for the help and explanation.

---

