---
title: "Manually Partition for Ubuntu Install?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by erikweho on 2006-10-28
Newcomer here has difficulty installing Ubuntu 6.10-desktop on Windowx XP-Pro machine. I get hung up at Step 5 of 6 selecting:
/dev/hda  IDE1 Master (hda). Basically the NEXT button refreshes and nothing happens. 

The Maxtor drive has four partitions. I'd like to install Ubuntu using the first partition that is also used by WIndowx XP-Pro. First Partition stats: 
File System NTFS, 
Size 24.41. GiB, 
Used 12.39 GiB (51%), 
Unused 12.02 GiB 49%, 
Flags BOOT, 
Path /dev/hda1.

Should I try to manually split the 24.41, using 12 GiB for Ubuntu? Additional info available if needed.

Thanks. --Erik;)

---

### Post by Craigus on 2006-10-28
> I'd like to install Ubuntu using the first partition that is also used by WIndowx XP-Pro.

You can't do that - each operating system must have its own partition. Additionally, Ubuntu will need a swap partition as well, and a /home partition is a good idea. What are the other partitions on the drive?

---

### Post by Kateikyoushi on 2006-10-28
You can't install ubuntu on an ntfs partition, have to make ubuntu it's own partitions at least a swap and a / partition.
You can find help about the installation here. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

