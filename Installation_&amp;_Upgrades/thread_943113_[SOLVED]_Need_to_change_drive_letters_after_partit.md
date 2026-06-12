---
title: "[SOLVED] Need to change drive letters after partitioning"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by gregkarr on 2008-10-09
I posted earlier on a Vista forum about how to shrink the Vista partition since i want to dual boot Vista and Ubuntu. That post is here:
[http://thevistaforums.com/index.php?showtopic=44464](http://thevistaforums.com/index.php?showtopic=44464)

The tip I got there was to use Gparted to shrink the Vista partition, and that is what I have done. The partitions I now ended up with are:
1: Boot(?), NTFS: My computer (Lenovo, Thinkpad W500) came with this partition preinstalled, and I have not modified it. Vista tells me that if I modify this the system won't be able to boot.
2: Vista, NTFS.
3: Ubuntu, ext3.
4: Linux swap.
5: Data, NTFS.

Gparted let me shrink the Vista partition and create 3, 4 and 5. The problem is that after doing that when I reboot, the drive letter for the Vista partition is E: and the drive letter for the Data partition is C:. With Vista not on C: it cannot start normally and only gives me a blank blue screen when I log in.

This poster seems to have found a solution:
[http://www.howtogeek.com/forum/topic/how-t...letter-on-vista](http://www.howtogeek.com/forum/topic/how-t...letter-on-vista)

I have downloaded MBRWiz64, and made a Vista repair disk, but I still don't know whether this is a good way to proceed. If it is, how do I wipe the first 63 sectors of the disk? Using MBRWiz64? (I tried to use MBRWiz64 to set the Vista partition as active, but on restart I just got the message "Bootmgr not found".) If I do this, is it safe to assume the Vista repair disk correctly assigns drive letters afterwards?

Or maybe I should do something else? Like use MBRWiz64 to somehow edit the MBR and thereby change the drive letters?

A couple of notes:
1. There is nothing important on my harddrive.
2. I don't have a Vista install dvd, only recovery and repair dvds/cds, so I *can* reinstall, but that would bring my computer back to the factory install which means I'd have to go through the partitioning all over again and probably would face the same problem.
3. I have *not* installed Ubuntu yet, only prepared the partitions. Maybe it's easier to take care of this problem after getting Ubuntu up and running?

Any help is much appreciated. Thanks for reading!

---

### Post by Ng Oon-Ee on 2008-10-10
AFAIK, recovery CDs do not usually affect the partitioning of your hard drives. They normally just use the data on the first partition (the partition is bootable and should contain the same data as your recovery CD/DVD) and install it into the second partition.

The recovery CD would be your best bet I think. That's what I would do, instead of messing around with MBRs, especially since you haven't yet set up Ubuntu.

Oh, and by the way, I have the same setup as you but place my NTFS Data drive just after my Vista drive, followed by my swap, my /home partition, and my root (/) partition. This was recommended by psychocats I think (there's a [website]("http://www.psychocats.net/ubuntu/") with that name with tutorials on Ubuntu basics), so that anything you do with linux won't need to affect your data (for example, repartitioning for bigger swap, merging /home and root to a single partition instead of dual partition, installing two different distros etc.

---

### Post by cariboo on 2008-10-10
Have you tried BCDEdit.exe to edit the Vista boot loader. It is part of Vista.

The way I usually set up a hard drive that I plan on dual booting is to create a partition to whatever size I need for windows and leave the rest of the hard drive blank, I then use the Ubuntu partitioner to create the partitions I need for installation manually while doing the installation.

Jim

---

### Post by gregkarr on 2008-10-13
I tried to use the solution referred to above and wiped the MBR. Not a good idea. The Vista repair cd only recognized the first partition, and since my Thinkpad came with a boot partition that Vista tells me not to mess with, that was the only one that showed up. 

So: my way around this was to do a complete factory recovery, and then completely avoid using Gparted to resize my Vista partition. The key to getting Vista to shrink the Vista partition was to use Perfect Disk 2008 to do an offline (ie. boot time) defragment of system files, then shrink however much Vista would let me, and then repeat. I continued this until I could shrink the Vista partition to its desired size. Then I installed Ubuntu and used the partition manager in the installation process (ubiquity?) to create the root and swap partitions. 

That worked out well, but now I'm encountering another problem that I'll post about in a new thread.

---

