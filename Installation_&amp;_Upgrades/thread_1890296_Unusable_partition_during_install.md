---
title: "Unusable partition during install?"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2011-12-03
I have been trying to install a new kubuntu 11.04 OS onto a friends laptop with windows already on it. 

During the install process we shrunk his windows data in order to create free space to put an extended partion table onto and then put swap, boot and home partitions on.

However after shrinking the NTFS partition succesfully the remaining space came up in the partitioner as "Unusable" and cannot be further manipulated.

Using the live cd we managed to create a new NTFS partion, but again in the install partitioner as soon we allocated 10 gigs for / partiton the remainder again became "unusable"

Has anyine else come up against this situation, and is there a fix, because it seems that we cannot install Linux on this laptop without first destroying windows, which he doesn't want to do at this stage as he has never tried Linux before.  (Iam very disappointed that this has happened, as it does not do well when extolling the virtues of our OS for this to happen on an initial install!)

Any help greatly appreciated.

---

### Post by Rex Bouwense on 2011-12-03
Can you post a screen shot of the partitions?  You realize that you can only have four primary partitions.  Microsoft Windows uses four so one of the partitions has to be deleted and an extended partition created on which you will be able to create any number of logical partitions.  
Now some where on this forum I read that the old four maximum partitions may be a thing of the past.  I thought that I had bookmarked it but it is lost until I search again.

---

### Post by tropdoug on 2011-12-04
Yes we knew that. After a lot of tries of deleting partitons, creating extended partitions and then splitting the extended into an initial OS partion of 10 gigs -- every time the remainder became "Unusable". 

That was until we went into windows and used their partition manager. Then we were able to create the extended partition - and 3 logical partitions all as NTFS. Having done that we then went back to booting the live CD and converted the 3 new partitions to Ext 4 -- /, /home and swap. 

Then the install went well. Seems a big let down that we had to go to Windows to fix the issue.

Thanks for the assistance though and hopefully it will be sorted in future releases.

---

### Post by MAFoElffen on 2011-12-04
> **Rex Bouwense said:**
> Can you post a screen shot of the partitions?  You realize that you can only have four primary partitions.  Microsoft Windows uses four so one of the partitions has to be deleted and an extended partition created on which you will be able to create any number of logical partitions.  
Now some where on this forum I read that the old four maximum partitions may be a thing of the past.  I thought that I had bookmarked it but it is lost until I search again.
Current Limit is still = 4 primary partitions or 3 primaries and a extended as the fourth. Within that extented, some say unlimited, while others say 512 logical partitions.

I often do the same as the OP has done for other people's computers --> shrink down a Windows primary. Shrink down the Windows Recovery Partition > Use the unused space as extended, with a logical ext4 and a linux swap.

I use a GParted LiveCD to do all my shrink/move, partitioning.  For Linux and Unix, I have a box where 1 disk has 18 partitions, all logical, all with bootable OS'es.

---

