---
title: "Partitioning...."
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by PPAAUULL on 2006-08-28
I am getting a new PC very soon and everything and I have been into Linux for about a year. I was wondering if the Ubuntu 6.06 install CD that was the first final release Install CD (not a beta) could resize my NTFS Partition with Windows XP on it, none destructivly (Without lossing anything). The reason that I just don't go straight Ubuntu is 'cause by brother loves windows and no matter how much I try he won't use linux so I need the windows on there ](*,). Anyways if you could help me with this that would be great. Thanks :D.

Paul

---

### Post by reacocard on 2006-08-28
yep. ubuntu has no problem with resizing ntfs.

---

### Post by Mike_N on 2006-08-28
First off, yes!

2nd... The current version of Ubuntu is 6.06.1 witch has many updates over the first release of Dapper Drake.

3rd... Ubuntu uses a partitioner called Gparted that does do non-destructive partitioning and if you'd like, you can download an ISO of it and boot into it any time you need to resize or create partitions. Great app...

Hope this helps, Mike

---

### Post by PPAAUULL on 2006-08-29
Thanks to both of you. That is great to know. I only wanted to ask seeing as I used to use Suse but switched to Ubuntu and even though suse coud resize partitions it couldn't resize ntfs. anyways thanks so much and I can't wait to get back on linux!!!!:D 

Paul

---

### Post by az on 2006-08-29
By default, the partitioning is simple:  if it detects a windows partition that it can resize (has free space, is not fragmented, proper partition table, etc...) it will ask you how small to shrink it.  That's it.  It will do all the rest for you unless you want to do it manually.

---

