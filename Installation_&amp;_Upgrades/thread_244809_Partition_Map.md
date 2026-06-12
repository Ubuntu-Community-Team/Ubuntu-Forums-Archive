---
title: "Partition Map"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by bstone on 2006-08-26
I have a MacBook with an internal 160gb HD (I just installed it). 100gb has OS X. I left 60gb as "free space". I want to use about 15gb for Ubuntu.

I tried to set the partitions manually but I know I am doing somethign wrong. Can someone please post what is exactly required for the parititon, including mount, /, boot, swap etc?

Thank you.

---

### Post by Herman on 2006-08-27
> I tried to set the partitions manually but I know I am doing somethign wrong. Can someone please post what is exactly required for the parititon, including mount, /, boot, swap etc? All you really need is one large 'root' partition, for example 14 or 14 1/2 GB, plus a small swap area of say 1/2 to 1 GB. 

Regards, Herman :D

---

### Post by bstone on 2006-08-27
I created two partitions. A 10gb EXT3 primary partition and a 1250mb ext3 swap partition. I kept getting the error of "invalid mount point" or some such.

Please advise!

---

### Post by Herman on 2006-08-27
> I created two partitions. A 10gb EXT3 primary partition and a 1250mb ext3 swap partition. I kept getting the error of "invalid mount point" or some such. Okay, are you following any of the good installation guides for the new graphical installer/partitioner?
This one might help you, [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
Especially look between the 10th to the 17th illustrations there and read the comments and maybe a click few of the links there too.

The ext3 main operating system partition, otherwise know as the 'root' (of the filesystem) partition, mounted as '/', can be on a Primary or a logical partition. Either one is okay for Linux, it's only Windows that's fussy about that.

The 'swap' area is for the memory, kind of like a 'page file' or 'virtual memory' in some other operating systems.
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)
I don't think it is meant to be formatted with a filesystem, just create the partition for it and mount it as a swap area. The pictures in the first link should show you how to do that.

---

