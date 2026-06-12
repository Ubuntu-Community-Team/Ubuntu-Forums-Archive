---
title: "be careful using fdisk on ubuntu 10.04: max 2TB partitions! RAID RAID5 RAID6"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by alfonso78 on 2011-10-15
Hi,

this is just a warning for something I've just learnt the hard way: be careful in using fdisk! 
As far as I understand, it cannot create partitions bigger than 2TB.

I copied and copied data on my RAID volume to find out it was full, so I had to start all over from scratch!

Only when cp complained there was no more space, I found out.

So after you create a new raid array with mdadm (in case you have a RAID setup like me) check the size of the partition you create and don't use fdisk.

To recreate the partition I did the following:

```
parted /dev/md0
mklabel gpt
```

to enable GPT on the partition [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

and then 

```
gparted /dev/md0 
```

to create a single partition that uses all the space in the disk (I couldn't quickly find a way in parted to say "use all space in the device").

Hope this helps someone!

---

### Post by CharlesA on 2011-10-15
You use GPT on anything larger then 2TB since the limit of the msdos partition table is 2TB - so +1. :)

I've been using gparted to partition drives smaller then 2TB for a while now as well (using GPT).

---

