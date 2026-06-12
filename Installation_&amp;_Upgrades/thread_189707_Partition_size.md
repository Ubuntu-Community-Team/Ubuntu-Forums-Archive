---
title: "Partition size?"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by mitchmcse on 2006-06-05
I am about to do a new install on a laptop that already has winxp on it and want to dual boot it.  How much space should I free up for the Ubuntu partitions? 10GB, 20GB?
Thanks

---

### Post by kb3hkg on 2006-06-05
At a minimum you will want a few GB's. 10GB would be more then enough, above that it depends on what you would want to install, save, and overall do with the partition as to how big to make it

---

### Post by mitchmcse on 2006-06-05
I am looking to just have a dual boot for now. Basic install with a few extra apps added and eventually have it as my only OS.  So I am taking it 10GB free space on the hard drive will be enough to create all the partitions and have plenty of free space left to add stuff later.

---

### Post by ubnoobie on 2006-06-05
10 gigs is more than adequate for what you're looking at.. 3-5 gigs would be a minimum for a full desktop install with a little room to breathe. 

after that, space you may need is dependant upon how much data you plan on sticking on the linux partition(s). for sharing data between the two operating systems, a separate fat32 partition works well. and don't forget to leave room for your swap partition.

my root partition is currently at 2.9 gigs used (of 15), with no data migrated over yet. i have a 1.5 gig swap partition and a 30 gig fat32 partition (an entire 2nd drive) for sharing data between windows & linux. my windows paritions are 5 gig (98se) and 12 gig (winxp), and i also have a fat32 'data' partition on the 1st drive. i do not mount the windows system partitions (use the 2 additional fat32 partitions for 'shared data').

---

### Post by mitchmcse on 2006-06-05
Ok, sounds like it will work. What I will do is create a 10GB unpartitioned space and let Ubuntu automatically create the partitions on it. Which I am assuming it will create the best sizes for it. The laptop has a 100GB drive with 1GB of ram.

---

### Post by mitchmcse on 2006-06-05
I am assuming 10GB free space will be enough for Ubuntu to create all the needed partitions and have space to install stuff later.

---

