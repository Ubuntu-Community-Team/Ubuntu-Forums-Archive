---
title: "Installer choosing wrong partition for dual boot"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by rknoblock on 2011-12-28
I have a Windows Vista system with three partitions: 41 MB FAT32 (sda1), 10 GB with the Windows Recovery D: drive(sda2), and 288 GB for the C: drive (sda3). I want to set it up for dual boot with the Windows partition split in two to be shared by Vista and Ubuntu. When I run the installer, it chooses the D: drive to be repartitioned instead of the C: drive. I have looked at the manual partitioning, but that would wipe out what is already on the drive.

---

### Post by hansdown on 2011-12-28
Welcome to the forum,rknoblock.

Your best bet, is to shrink the partition of your choice, with windows.

Next, defrag, and defrag, again.

Then, do the install, choosing the partition you would like.

---

### Post by Mark Phelps on 2011-12-28
Agree with hansdown -- use Windows to shrink the OS partition, don't let the Ubuntu installer do this.

To do this in Windows, open the Disk Management utility, select the OS "drive" (Windows calls them drives, not partitions), and shrink the size.  When done, reboot into Vista a couple of times to let the filesystem make any needed adjustments.

Do NOT format the newly unallocated space in Windows; instead, use the Ubuntu installer to do that.

---

### Post by Bucky Ball on 2011-12-28
> **hansdown said:**
> Welcome to the forum,rknoblock.

Your best bet, is to shrink the partition of your choice, with windows.

Next, defrag, and defrag, again.

Then, do the install, choosing the partition you would like.

Agreed. Let Windows do the shrinking. But I would do the two things above in reverse order. Defrag and defrag again, *then* shrink the partition. If you don't do this you can get unreliable information on how much you can shrink the partition (as Windows throws data around all available space and defragging will bring it all together).

Not sure of the point of defragging *after* you've shrunk the drive ... pulling all the info into the smallest space possible before shrinking is the reason for the defragging (there is better defragmentation software around than the generic Win one also, Power Defragmenter I think is the one I used last time I had to do this). ;)

---

### Post by hansdown on 2011-12-28
> **Bucky Ball said:**
> Agreed. Let Windows do the shrinking. But I would do the two things above in reverse order. Defrag and defrag again, *then* shrink the partition. If you don't do this you can get unreliable information on how much you can shrink the partition (as Windows throws data around all available space and defragging will bring it all together.

Not sure of the point of defragging *after* you've shrunk the drive ... pulling all the info into the smallest space possible before shrinking is the reason for the defragging (there is better defragmentation software around than the generic Win one also, Power Defragmenter I think is the one I used last time I had to do this). ;)

That does make more sense.

Thanks.

---

### Post by efflandt on 2011-12-29
Defragging **before** shrinking is spot on, possibly temporarily disabling virtual memory (which cannot be moved) before that.  When I first got a computer in 2004, I was only able to shrink my WinXP partition by 24 GB (using ntfsresize at that time) for SuSE and to try 64-bit WinXP beta.  Many years later by temporarily disabling virtual memory (requires reboot) and defragging first, I could have freed up over 150 GB with gparted, but did not need that much for Linux.

Vista and Win7 have their own utilities in Disk Management that would best do the shrinking of their own partitions.

---

