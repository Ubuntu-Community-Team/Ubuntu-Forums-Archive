---
title: "[SOLVED] fsck failure exit status 8"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2007-11-09
I believe that I may have both caused this and solved my problem. I have two drives, both Gutsy. I was trying to move files between the two and in former times, had instructions for doing that. The last line (now commented out) was that instruction. On nano-ing the line with ##, the OS restarted without problem.

Of the 2 posts that discuss "fsck died with exit status 8" both have "0" replies. But here I go anyway.

This is a brand new motherboard & cpu. Same hard drive, but newly installed Gutsy Desktop (tribe 2). It has been completely updated this morning. When powered up, the boot runs as far as the fsck and dies. 

What causes this? Can I use the CD to wipe then entire harddrive and try again?

My fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0fe55993-b869-4a83-9c32-f17d4617bb3c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=89e97a5c-4907-46f4-80eb-376f871c1d49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

##Added by mp on 11/9/07
##/dev/hdb1 /mnt/Drive2	ext3	defaults	0	2

---

