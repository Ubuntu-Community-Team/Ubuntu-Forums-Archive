---
title: "Multi-Boot"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by Skywalka443 on 2007-02-14
Nvm, if i would have read a little more I would have found a thread about this.

---

### Post by IgnorantGuru on 2007-02-14
I'll give you a short answer - maybe someone else has a howto for the details...

You can read my partitioning suggestions here...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

Install XP first.  When you install Ubuntu, it will want to erase the hard drive by default.  Instead, select to manually edit the partition table, and set your mount points (/ to one partition, and swap to another, at least).  Ubuntu will 'see' your XP partition and will install grub - which makes the system multi-boot.

Linux will read NTFS, and with some extra drivers will write to it.  It will also read/write FAT32 partitions.

Windows will not natively read or write linux partitions (ext2, ext3, or reiser).  You can add a driver that will enable it to r/w ext2&3.

If you want a partition for data that is shared by both, FAT32 is probably the easiest way to go - will work out of the box on both, no additional drivers.

If anything in that isn't clear please ask.

---

### Post by Skywalka443 on 2007-02-14
[http://www.ubuntuforums.org/showthread.php?t=360134](http://www.ubuntuforums.org/showthread.php?t=360134)

I moved my problem there because it was pre-existing and i didnt want to make another thread on the same topic. That has got my current situation on it.

Thanks

---

