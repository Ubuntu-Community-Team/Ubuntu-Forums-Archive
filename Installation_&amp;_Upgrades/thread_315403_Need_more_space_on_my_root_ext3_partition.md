---
title: "Need more space on my root ext3 partition"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by Jadd on 2006-12-09
I've got the same problem as [candyoff](http://www.ubuntuforums.org/showthread.php?t=286085), but I didn't want to hijack his/her topic. I need to resize my root ext3 partition. After running out of disk space and being unable to load gnome (I had to delete files using the ctrl-alt-f2 terminal), I realised I needed to make my root partition much bigger than 3 gig.

Currently, this is how things stand:
1 NTFS partition (Windows XP)
1 NTFS partition (Windows XP)
1 FAT32 partion
Unallocated space (several gig)
1 ext3 Linux root partition
1 Linux swap partition

I loaded Ubuntu Dapper live CD, and ran gparted. It claims it can resize my ext3 partion, but only on one side, on the right (the swap partition) to the left, making it smaller! I can't take advantage of my allocated space before the ext3 partition.
Help! ](*,)

---

### Post by bulldog on 2006-12-09
I don't think you can do it because the free space is in front of your ext3 partition.
You can make a separate /home in the free space you have.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

By moving your /home to a different partition you should make a valuable space for / [root].

---

### Post by Jadd on 2006-12-09
So resizing the ext3 to make it take advantage of the space in front of it is definately not possible?

---

### Post by bulldog on 2006-12-09
Not as far as I know,but take a look at the gparted site,maybe is there something useful to find.

---

### Post by louieb on 2006-12-09
Since your out of space and it broke any way Here is a suggestion.
IF the free space in front of the Ubuntu install is large enough to hold the Ubuntu install. Why not create a partition out of it and use PartImage to copy your Ubuntu install to it. if that works then it just a matter of changing menu.lst to reflect the change in partition location. After that is done then maybe GParted can resize the new partition. 

But you may not want to listen to my suggestion since the last time I used GParted was setting up a PC for dual boot and completely trashed the XP installation and had to reinstall XP from scratch.   
      
I have been running Ubuntu Linux since June 2006 and have separate /boot, / and /home partitions. But by way of example here is my current disk usage now on my P2 400 (not the machine I trashed XP on that was the P4).
```
lou@gameu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             9.7G  3.0G  6.2G  33% /
dev/hda1              59M   23M   34M  40% /boot
/dev/hda4              18G  2.3G   15G  14% /home
/dev/hdb1             7.9G  4.0G  3.9G  51% /media/windows
```
hda Ubuntu,  hdb XP

---

### Post by bulldog on 2006-12-09
Hi louieb,that is a good idea in fact,didn't think about that myself :D 
It all depends on how much the free space is.
But I like your suggestion.

---

### Post by Jadd on 2006-12-11
Good idea, louieb.
Would it be easier to just install Ubuntu on an ext2 partition? Can I resize ext2 partitions in any directions I want? What are the main disadvantages of ext2 compared to ext3?

---

### Post by bulldog on 2006-12-11
It won't go with any file system,as far as I know.

---

### Post by Jadd on 2006-12-11
Problem solved! Downloading the latest gparted live CD (version 0.3) fixed it. It could resize my ext3 partition both ways. Thanks louieb and bulldog for your help.

---

