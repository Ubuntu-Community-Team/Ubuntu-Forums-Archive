---
title: "installing Ubuntu on Vista with multiple drives"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Andrew Golightly on 2009-11-26
Hi there,

I'm trying to install Ubuntu on my brother's computer. He has Vista on it and wants to dual boot. The Ubuntu partitioner gives me two options... 1) delete the whole disk and install Ubuntu, or 2) manually partition. I don't really know enough about 2 to do that. I'd like to have the resize 'x' and install Ubuntu option back :D Is this too complicated because of his drives?

Attached in the screen shot of his partitions from Windows Vista. How can I get Ubuntu installed for him? :-k

thanks,
Andrew

---

### Post by arubislander on 2009-11-26
From the look of things your brother already has 4 primary partitions on his machine, so there's no room for any more. that is why the 'resize x' option is missing. Even if you did resize one of the partitions, you still would not be allowed to create a new one.

Your best bet is to make a backup of all his data, delete the third partition (the one labeled (D: ), create an extended partition in its place, then create a logical partition that's say 50 GB as his new D:, restore the data and then try the install again. It should give you more options.

But before you do all of this please make sure
a. You've backed up all his data
b. He has a windows recovery CD
c. You've backed up all his data
d. You know how to recover the OS and the Data in event of disaster
e. You've backed up all his data
f. You're comfortable partitioning a hard drive

O, did I mention to back up his data?

---

### Post by darkod on 2009-11-26
The previous poster said it all, just to add something:
If you don't need the 3GB partition I would recommend to delete that too. Few people who have reported dual booting problems here that I tried to help, had some kind of similar restore/utility partition at the back of the drive. I am not 100% but I started developing a "theory" that having the utility partition on the back of the drive is actually their problem with dual booting. To be more precise, after they installed ubuntu, it was working fine, but if you select windows (any version) in the grub menu windows would not boot.
Some of them deleted the partition and that sorted out their problem but at this point of time I can't be sure that's a general fix.
The 10GB partition is probably restore partition and I don't know what the 3GB is. Unless it's REALLY important I would consider deleting it.
Even after shrinking current D: (as the other poster suggested), you will still have the 3GB at the end of the drive, after your extended partition, and probably a message in fdisk -l that the partitions are not in order.

---

### Post by Andrew Golightly on 2009-11-27
Thanks. My brother is having a think about what he would like to do.. He's thinking of maybe getting the Ubuntu installer for Windows for now.. that might be simpler.

Thanks for both your inputs.

A

---

