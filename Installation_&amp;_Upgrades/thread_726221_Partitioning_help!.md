---
title: "Partitioning help!"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by LiviooT on 2008-03-16
I currently have a 240 GB Hard Drive formatted NTFS and partitioned as shown below:

[http://img110.mytextgraphics.com/photolava/2008/03/16/wtf-49utz9fc8.jpeg](http://img110.mytextgraphics.com/photolava/2008/03/16/wtf-49utz9fc8.jpeg)

I want to install Ubuntu on a 100 GB partition by splitting the large, Media (E), in half. I use Norton Partition Magic for this because quite frankly I am a little scared of running the Ubuntu partitioner :). 
The problem is that the Large partition is registered as an extended one wrapped around my logical partition (like in the screenshot) and this prevents the Norton PM to split it (and any other partitioner as far as I know...). SO... how exactly do I split that partition?... can I "unextend" it? thank you very much and try not to include technically challenging answers... I am kind of a noob in Linux...#-o

---

### Post by sandysandy on 2008-03-16
logical  or extended  seems to be the same partition. if u add up the disk space of logical / extended and C;/  it will add up to ur total disk space.

have u tried gparted live CD. its good.

regards

---

### Post by sandysandy on 2008-03-16
to quote wikepedia
> 
A PC hard disk can contain either as many as four primary partitions, or 1-3 primaries and a single extended partition. Each of these partitions are described by a 16-byte entry in the Partition Table which is located in the Master Boot Record.

>  An extended partition is secondary to the primary partition(s). A hard disk may contain only one extended partition; which can then be sub-divided into logical drives, each of which is (under DOS and Windows) assigned additional drive letters. 

have a look at these links

[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

[http://en.wikipedia.org/wiki/Partition_(computing](http://en.wikipedia.org/wiki/Partition_(computing))

with gparted u can make additional partitions after resizing existing one.

regards

---

### Post by LiviooT on 2008-03-16
So If I use the Live CD or the gParted CD to say... split the partition in half or make a 100 GB partition inside the extended one... will this corrupt my windows installation?I really need my windows installation... :| what exactly is the role of the extended partition on my configuration? does it just wrap around the Media logical drive? Is it safe to resize the partition inside it so that I can install Ubuntu? thx a lot man :)

---

### Post by sandysandy on 2008-03-16
i assume that ur windows is on C;/ drive.

that being so when u create further partitions in E;/ extended partition it should not affect ur C:/ drive. do u have anything on E:/.

in any case backup important data.

regards

---

### Post by sandysandy on 2008-03-16
have a look at this link on how to use gparted

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

regards

---

