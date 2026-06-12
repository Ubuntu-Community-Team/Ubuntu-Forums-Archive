---
title: "Questions on partitioning disk with hidden recovery partition"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Riverglen on 2008-04-20
I have a new Acer machine, running Win-XP Pro. As delivered, the machine was set up with three partitions, as follows:

~6 GB Fat32 - Hidden, evidently a recovery image
~71 GB NTFS - The Windows C partition
~71 GB Fat32 - Evidently intended as a backup, used by Acer's bloatware "empowering
technology"
~4GB unallocated space.

I want to install Ubuntu 7.10, using part of the space that was allocated to the backup partition. I had intended to recover that space and allocate most of it back Windows and save 10-15 GB for Ubuntu. I used a stand alone version of GParted (which may not be the most recent available version?) to delete the D partition, and was on the point of then extending the Windows C partition to fill part of the freed up space. However, when I had specified the new size for the enlarged C partition, I noticed that GParted said it was going to "move the C partition to the right and extend it" and the pending map for the drive showed a new small amount of unallocated space between the 6GP Fat32 and the apparently relocated start of the Windows C partition.

So my question is, if I had gone ahead and done this, would it have screwed up my Windows partition? I was afraid it might, and in any event, why put a sliver of unallocated space in front of it? Will the partitioning tool in the Ubuntu Live CD install wizard handle this safely if I use it to extend the Windows partition?

Also, in sniffing around in this forum is found at least one person who did an install on an Acer machine and wound not being able to boot windows.  The machine tried to boot into the recovery partition evidently, it being the first partition on the disk.  He got some advise to solve the problem, but I'd prefer not to have to undergo the melodrama.

I took a look at the XP Disk Management tool, and it evidently will not allow you to mess with the partition that contains Windows.

---

### Post by Riverglen on 2008-04-21
Bump

---

