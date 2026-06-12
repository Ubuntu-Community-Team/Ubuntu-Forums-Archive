---
title: "Help with RAID configuration"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by brickhead248 on 2012-01-05
Hey Ubuntu Forums, long time no see.
So i'm trying to set up a RAID, but i'm a bit inexperienced and i'm not sure if the configuration i want to achieve is possible. I was hoping someone more knowledgeable could point me in the right direction.

I have one 2TB and two 1TB drives that i would like to configure in such a way that would be equivalent to two 2TB drives in RAID0. 

My MSI K8N Neo2 motherboard has an onboard raid thing, this is what the website says about it:

• NV RAID (Software)
• Supports up to 4 SATA & 2 ATA133 Hard drives
- RAID O or 1, 0+1, JBOD is supported
- RAID function work w/ATA133 + SATA H/D or 2 SATA H/D

Thank you :3

---

### Post by darkod on 2012-01-05
You can't use RAID0 with 3 disks. It has to be even number, like 2, 4, 6, etc.

And are you sure you want to use raid0 at all? Your data is not protected in raid0, if one disk fails, everything is gone.

What are you trying to achieve?

PS. Also, do you plan to dual boot with windows or only ubuntu? For dual boot the options are more limited.

---

### Post by brickhead248 on 2012-01-05
Thanks for the reply. Sorry, I meant to say RAID1. I want all my files on the 2TB to be automatically repeated on the two 1TBs

---

### Post by brickhead248 on 2012-01-05
Also I have a 500GB drive that I can use to store the filesystem, if that's needed.

---

### Post by Buntumatic on 2012-01-05
Yea you can do that. For instance: 
You can create RAID0 on two 1GB drives and RAID1 on 2 GB drive + previously created 2 GB RAID0.
Forget the motherboard "RAID", it's fake. Use mdadm.

---

### Post by darkod on 2012-01-05
> **Buntumatic said:**
> Yea you can do that. For instance: 
You can create RAID0 on two 1GB drives and RAID1 on 2 GB drive + previously created 2 GB RAID0.
Forget the motherboard "RAID", it's fake. Use mdadm.

Would this be a better option or creating two equal partitions on the 2TB disk and two separate raid1 arrays using these partitions and each of the 1TB disks?

---

### Post by brickhead248 on 2012-01-05
Ok, thanks :3 RAID1( RAID0(1 TB,  1TB), 2TB ) (if that makes any sense) sounds good. How do I do that? :S

The nVidia raid thing didn't look like it supported stacking raids like that.

---

### Post by darkod on 2012-01-05
First of all, to have raid support you need to install with the alternate install cd, not the standard desktop image.

I have never stacked raid like that either, but the idea would be like:
1. During the install in the partitioner create a single primary partition on both 1TB disks taking the whole disk. Set the partition type as RAID. Go in the Configure Software RAID option at top, and configure a raid0 raid device from the two partitions on the two disks.
2. That should show a new raid0 device in the partitions list. Now create one single partition on that device taking the whole space of type RAID also. Create single partition on the 2TB disk type RAID. Go again in Configure Software RAID and create a new raid1 device from the above partitions.

That should be it. Not sure how it would work though. :)

---

