---
title: "inspiron 6400: Bad primary partition 3: Partition ends in the final partial cylinder"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by hypermegachi on 2007-06-08
i just got a new laptop, dell inspiron 6400.

it's partition table is set up this way:
1) a 55 meg partition which is supposedly the dell boot utility
2) a 10 gig recovery partition that contains the completely original HD
3) a 81 gig partition which has Vista on it
4) a 2 gig partition for MediaDirect

i used dd to backup the 10 gig partition, and was about to install linux.  cfdisk craps out with the error message:
"FATAL ERROR: Bad primary partition 3: Partition ends in the final partial cylinder"

ok...i'm stuck.  gparted is able to go in and see all the partitions as fine, and it can delete partition 2, but if i try to format a new volume, it craps out.

now here's the kicker.  if i go into vista and into computer management, i can go there, format the 10gig to ntfs and it works fine.

any ideas?  thanks.

---

