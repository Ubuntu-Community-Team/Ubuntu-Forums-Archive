---
title: "Backing up DellRestore/DellUtility to free up Partition"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by imran7567 on 2007-07-13
OK, I am trying to install Ubuntu on my Dell Inspiron 6400 which I am currently running windows on. I have defragged and partitioned the free space from my windows drive to make room for the install. I have a problem though, with the pre-installed Dell recovery partitions. It seems, and I am sure you guys are aware, that Dell has a ghost image incase I need to recover the computer to as-shipped state. This partition is ~4 gb. My windows drive is 106 gb, out of which I will devote 10 to Ubuntu. But the problem is I have too many primary partitions. As I understand it, I can only have 4 primary partitions at a time. So here are the current partitions I have:

-Windows (NTFS)
-DellRestore (FATXX)
-DellUtility (FATXX)
-Free Space (ext3, going to use for ubuntu install)

When I run GParted I am unable to make 1 more partition for the swap space, since it gives me the "too many primary partitions" error. Now, I definitely want to keep the Dell related stuff since it might come handy some day. But how can I dual boot if it leads to so many partitions. I am sure other people with Dell notebooks would have experienced this and came up with a solution. I have searched the web but I can't find any *good* guides. I am willing to back up the Dell stuff onto bootable dvd if that is possible. If I have to do that can you guys please give me instructions (like I am a 6 year old, really sorry for noobiness). 

And, regarding the Dell recovery system, wondering if anyone knows if re-sizing the windows drive (fudging the original partition tables) will ruin the DellRestore process. Ok, please your help is very much appreciated. Thanks in advance.

---

### Post by al_erola on 2007-07-13
Your "free space" partition can be set up as an Extended Partition within which you can create a number of Logical Partitions.  Your might want to read up on this concept.  

The Ubuntu install process will allow you to create the extended partition and the logical partitions.  You should first to resize the Windows partition with another utility that handles NTFS partitions.

As for keeping the Dell restore and utility partitions that's you choice.  Did you got  several system restore disks with your Dell?  They still provide them where other vendors don't.

I've restored Windows OS and drivers from the Dell recovery CDs just fine when I've replaced a laptop hard disk.  That would solve the problem of resizing the extra Dell partitions.

Always backup any "user product."

Good luck.

---

### Post by imran7567 on 2007-07-13
> **al_erola said:**
> Your "free space" partition can be set up as an Extended Partition within which you can create a number of Logical Partitions.  Your might want to read up on this concept.  

The Ubuntu install process will allow you to create the extended partition and the logical partitions.  You should first to resize the Windows partition with another utility that handles NTFS partitions.

As for keeping the Dell restore and utility partitions that's you choice.  Did you got  several system restore disks with your Dell?  They still provide them where other vendors don't.

I've restored Windows OS and drivers from the Dell recovery CDs just fine when I've replaced a laptop hard disk.  That would solve the problem of resizing the extra Dell partitions.

Always backup any "user product."

Good luck.

al_erola, I really like your idea because it seems like the simplest solution at this point. But let me make sure I understand this correctly. I will resize my widows partition and create some free (unallocated) space. So I now have 3 primary partitions (windows, dell1, dell2). I now run the ubuntu LiveCD and during the install process I choose to manually partition the drive. Now out of that 'free space' I can create a partition for linux OS (ext3) and swap space? Does this mean they will both be extended and logical? I guess this way I can prevent going above the limit of 4 *primary* partitons...

---

