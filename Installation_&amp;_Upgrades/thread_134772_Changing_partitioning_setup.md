---
title: "Changing partitioning setup"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by dmh-bidlah on 2006-02-22
I hace currently set up a dual boot of Ubuntu Breezy Badger and Windows XP. I have a 40 GB HDD. Currently the partitions are set up as:

/dev/hda1 20GB Windows
/dev/hda5 40MB /boot ext2
/dev/hda6 8.5GB /home c
/dev/hda7 6.7GB / ext3 
/dev/hda8 512MB swap

Now that I have gotten used to Ubuntu I have decided to shrink the Windows partition down to 10GB, and enlarge the /home partition. 

to
/dev/hda1 10GB Windows
/dev/hda5 40MB /bootext2
/dev/hda6 18.5GB /home ext2
/dev/hda7 6.7GB / ext3 
/dev/hda8 512MB swap

But what would be the best way of doing it? I have some valuable data on /home that I don't want to lose. I don't care much about the / partition.
Does reinstalling Windows XP erase my partition data? Is it possible to prevent it? Is the Ubuntu partitioner capable of nondestructive partitioning?
Thanks...

---

### Post by Ocxic on 2006-02-22
there is really no way of doing this without reformatting, scince the partitons you want to change are set inbetween others you wont be able to resize them.

---

