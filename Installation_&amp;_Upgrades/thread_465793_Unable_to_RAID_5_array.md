---
title: "Unable to RAID 5 array?"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by richmulhern on 2007-06-06
I had an old file server that I decided to turn into a MythTV box. The machine has 8 300GB hard drives on RAID 5 giving me about 1.8TB of space. When I get to the Ubuntu partition screen I get lots of weird problems. I can create a swap partition fine, I can create a / partition fine, but when I want to allocate the rest or a decent chunk of the rest (like 200GB+) strange things happen. I get a "can't have the end before the start" error and then it does nothing or sometimes it makes the partition but at a random size. Literally random, sometimes it will make the partition as small as 8mb.

So I tried using gparted instead. More strange occurances. For size I get -399093458432.00 B. When I try and size a partition I type in any size large or small and it resets to the default value that field, which here is -380603  MiB. 

Any ideas? Thanks.

---

### Post by racermd on 2007-06-09
> **richmulhern said:**
> ...I can create a swap partition fine, I can create a / partition fine, but when I want to allocate the rest or a decent chunk of the rest (like 200GB+) strange things happen. I get a "can't have the end before the start" error and then it does nothing or sometimes it makes the partition but at a random size...

I have the same problem on different hardware.  I've got a 74GB SATA disk (WD Raptor) that I'm setting up to boot from and a 400GB SATA2 (Seagate-something) that I'd like to use for storage.  I, too, can set up / and swap on the 74GB disk.  But I get the "Can't have the end before the start" message when setting up a large partition on the second disk.

Even if I try to fill the second disk with nothing but a / partition, it'll give me that error.

For now, I'll make due with a pair of smaller partitions to store data on.  I'll have backups made (don't you?) so I can re-partition this later, if anyone can figure out the problem.

Thanks in advance!

---

