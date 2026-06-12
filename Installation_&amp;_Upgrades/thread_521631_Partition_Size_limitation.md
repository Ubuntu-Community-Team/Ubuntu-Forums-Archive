---
title: "Partition Size limitation?"
date: 2007-08-09
forum: Installation &amp; Upgrades
---

### Post by aharvey on 2007-08-09
Hello, encountering an odd error.

I have a new computer here, and the ubuntu installer will not let me create a partition bigger than 200gigs.

Im running a RAID 5+0 config, Ubuntu recognized my raid card without a problem, and even relays the proper amount of unused space.

Now i know that ext3 has some limits depending on block size, but not allowing even a 500gig partition seems odd to me, anyone else ever encounter this?

Thanks in advance.

---

### Post by kidders on 2007-08-10
Hi there,

I've had problems with the Ubuntu installer in the past, and have gotten into the habit of not using its disk partitioner. In your case, there's a strong argument for not using it, considering that you intend to use Ext3 on a RAID array that involves striping ... something that can benefit greatly from a manual configuration.

Afaik, the upper limits on the size of the average Ext3 partition is between 16 and 32 TiB, so 500GiB really ought to cause you no trouble at all. I would suggest creating your target filesystems *before* running the installer.

---

