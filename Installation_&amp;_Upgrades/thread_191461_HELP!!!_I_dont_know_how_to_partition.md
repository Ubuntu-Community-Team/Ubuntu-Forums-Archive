---
title: "HELP!!! I dont know how to partition"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by maddbaron on 2006-06-07
Ok I am doing a dual boot install. my windows is already set.

I have three fat32 partitions for windows i think, the smaller of the partitions is 2.93 and i have 1.09gigs left unused that one is hda1 the other two windows parts are hda2 and hda3, 26.39 gigs and 12.17gigs respectively.

That leaves a 14.39 unallocated amount of space. I right click it i get many after i press new. 

it says create as new primary partition, which cannot be changed to logical or extended. it says zero mb free space preceding and  new size(mb) 14739 then after that it says free space following(mb) zero.

it says filesystem ext3 but has many options to choose from when i click that box.

so I am stuck as to what to do now i read online linux needs 3 partitions
/root
/home
swap

so how do i do that with the unallocated space of 14739gigs?

i would like to shrink one of the windows drives a little and give ubuntu more space.

but how do i set things up for the partition?

I am so lost...

---

### Post by tonyr on 2006-06-07
I'd suggest not worrying about resizing your Windows partitions yet.  You can use the 14+G
of unused space for the Ubuntu partitions.  Here's a link to a good partioning HOWTO:
[http://www.psychocats.net/ubuntu/partitioning.html]("http://www.psychocats.net/ubuntu/partitioning.html")

---

### Post by morequarky on 2006-06-07
I see issues with primary and logical.  You can only have four primary partitions.  You already have three I am guessing.

I have two primary partitions.  One for windows install and one for '/'.  The other partitions for my windows and linux are in logical partition space.

A drive can only have four primary partitions.  One primary partition will be the logical space.

1 primary windows.
2 primary logical - more partitions in here as logical
3 prmary linux '/'
4 primary logical - more partitions in here as logical

OR
1. primary windows.
2. primary linux '/'
3. primary logical - the rest of the partitons here as logical

You can only have four primary partitions.

---

