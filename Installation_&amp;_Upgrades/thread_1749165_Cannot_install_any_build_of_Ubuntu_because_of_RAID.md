---
title: "Cannot install any build of Ubuntu because of RAID0"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by Cr4z33 on 2011-05-04
It is such a pity I cannot install Ubuntu into my computer.
The only way to enjoy it is to run it under VMware...

Basically I have a RAID0 array with installed 2 NTFS partitions:

[LIST]
[*]Partition 1 has Windows 7 32 bit
[*]Partition 2 has Windows 7 64 bit
[/LIST]
Now I want to install Ubuntu 11.04 64 bit into a 3rd partition.
GParted failed to do the job by not recognizing the RAID0 content (it showed one uknown NTFS partition...). I tried the program both from Ubuntu Live CD and GParted Live CD/USB.

I then tried with the alternate Ubuntu installer and when at the partitioning step it miserably failed to create the ext4 and the swap partitions, although it recognized and showed the 2 NTFS partitions.

What's more it wasn't able to install GRUB, neither in the Linux partition nor in any of the Windows partitions.
I thought nowadays Ubuntu could be installed flawlessly on RAID0 systems, but what a nightmare...
I need please help. :(

---

### Post by Cr4z33 on 2011-05-05
Nobody cares? :confused:

---

