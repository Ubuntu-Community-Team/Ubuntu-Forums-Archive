---
title: "best speed between two hard drives nonraided"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by proselyte on 2006-09-10
I have a laptop, which doesn't have raid (hp dv8000t), two 80 gig hard drives.  Which partitions would go on which hard drive to have the best speed?
Also, i want to have an additional experimental install of ubuntu, so that if i try something new (compiz) then it won't break the main install
So, to save space, which instllations are either very easily backed up or almost certainly not going to be broken by something i do.  

lastly, if there is a way to add raid to my laptop, what is it

---

### Post by Original Brownster on 2006-09-10
Hi,
Ensure your disks are on different channels, I don't think you'll gain much speed but put swap on different disk/channel. 

With 2 disks you can use software raid which is supported in the 2.6 kernel, look at striping, RAID 0 , no redundancy but the data is spread over 2 disks and therefore twice the throughput is possible, at least in theory.

Check the specs' for your disks to see what speeds and ATA standard they support and make sure the disks are in DMA mode not PIO. If they are they can be tweaked, look at HDPARM

Your best bet for a complete recovery is 'MONDO' it's in the archives and will allow you to nuke and recover the entire disks or selectively.

HTH

---

### Post by proselyte on 2006-09-10
> **Original Brownster said:**
> Hi,
Ensure your disks are on different channels, I don't think you'll gain much speed but put swap on different disk/channel. 

With 2 disks you can use software raid which is supported in the 2.6 kernel, look at striping, RAID 0 , no redundancy but the data is spread over 2 disks and therefore twice the throughput is possible, at least in theory.

Check the specs' for your disks to see what speeds and ATA standard they support and make sure the disks are in DMA mode not PIO. If they are they can be tweaked, look at HDPARM

Your best bet for a complete recovery is 'MONDO' it's in the archives and will allow you to nuke and recover the entire disks or selectively.

HTH

Whoa thats complicated
Well, the hard drives are each 5400 RPM SATA
I have 1 gig ram (for gaming) so swap is practically a nonissue.  I think the main issue is the operating system, programs, and possibly home folder...but im not sure what some of the other folders are, and how much they are cached into ram

Also, since it must also run windows, whatever raid system must be windows compatible.

---

