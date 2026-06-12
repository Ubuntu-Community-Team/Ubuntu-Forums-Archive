---
title: "Help with Windows/Linux 2 disk partition scheme."
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by MindRiot on 2007-04-27
This is the partition scheme I would like to use:

Disk 1 (hda)  = 75 GB

Partition 0 = Windows XP = 50 GB
Partition 1 = Linux / (root) = 25 GB 

Disk 2 (hdb) = 19 GB

Partition 0 = Linux /boot = 50 MB
Partition 1 = Windows XP  page files = 2,420
Partition 2 = Linux /swap = 1,530 MB
Partition 3 = Linux /home = 15 GB

What do you think? Would moving the Windows page files to the slave drive improve performance, or would it remain the same or perhaps degrade performance? Does it even make sense to move the page files to the slave drive?

Before I can try this partition scheme, I'm faced with the following conditions:

Since I have reinstalled XP on my computer well over 25 times (don't ask, its not Windows fault), I suspect Microsoft might refuse to activate the product now that Vista has been released, and I'm not willing to lose Windows XP,  nor am I interested in buying a vista upgrade.

I like Ubuntu just fine, but I'll keep Windows XP all the same, thank you. So even though the Windows XP E.U.L.A. states you can use Windows indefinitely on single/same computer, it doesn't state you can reinstall it an unlimited number of times on said computer. In my book, the ability to use the OS indefinitely on the same computer would imply I could reinstall it over and over again, in perpetuity, on the same computer, but I have a hunch both Microsoft and the law won't see it that way.  They could draw the distinction nonetheless.

So my question is; "How likely am I to corrupt the Windows filesystem if I resize the partition using gparted?  I will definitely defragment the drive, and disable the page file first. I'm not sure if running fixmbr would do diddly squat from recovery console before loading Windows after resizing the partition, what do you think?

I also need to know how to move the Windows page files to the partition on hdb. Does anyone know how to do this or provide me a link to a howto?.

---

### Post by dcstar on 2007-04-27
> **MindRiot said:**
> 
.........
What do you think? Would moving the Windows page files to the slave drive improve performance, or would it remain the same or perhaps degrade performance? Does it even make sense to move the page files to the slave drive?
........
So my question is; "How likely am I to corrupt the Windows filesystem if I resize the partition using gparted?  I will definitely defragment the drive, and disable the page file first. I'm not sure if running fixmbr would do diddly squat from recovery console before loading Windows after resizing the partition, what do you think?

I also need to know how to move the Windows page files to the partition on hdb. Does anyone know how to do this or provide me a link to a howto?.

Yes, Swap/Page files on separate drives do improve performance - but only if the Swap/Page file is significantly used.

Just create a NTFS partition on the second drive and Windows will recognise it and allow you to allocate Page File space on it.

As far as resizing NTFS partitions, I have done it with no problems but do a Defrag first.

---

### Post by lw5 on 2007-04-27
> 
What do you think? Would moving the Windows page files to the slave drive improve performance, or would it remain the same or perhaps degrade performance? Does it even make sense to move the page files to the slave drive?


In theory yes, moving data between disks is faster than moving data between partitions. It should be even better if you use separate IDE channels for the two disks.

why bother with the /boot partition?

---

### Post by MindRiot on 2007-04-27
> **dcstar said:**
> Just create a NTFS partition on the second drive and Windows will recognise it and allow you to allocate Page File space on it.

I don't think gparted can format NTFS.  Am I wrong?  If gparted can't format NTFS, does anyone know a partition program I could use free of charge (freeware)?    

EDIT:  Actually, I think I could use Windows Disk Management under the Management Console to format an empty partition NTFS.


> **lw5 said:**
> why bother with the /boot partition?

I suppose to help keep things simple and safe.  Could do without I suppose.

---

