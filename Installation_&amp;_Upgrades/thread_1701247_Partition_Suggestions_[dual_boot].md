---
title: "Partition Suggestions [dual boot]"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by Meetloaf13 on 2011-03-06
Hello,

It's been a while since I last ran Linux, and I'd like to get back into the game.

I am going to dual-boot with Win7.  I have a HDD with 476 GB of memory.  I am in the process of backing up and imaging the drive before I proceed.

Before I install, I will have delete all the muck-partitions from the OEM, and will be left with 
- 200 MB System partition
- 86 GB Windows NTFS Partition
- ~315 GB Files NTFS Partition

This leaves me up to ~70 GB to play with for this installation.

If I remember correctly, I can only make one more partition on my drive or Windows will get fussy.

I'm just curious the best way to proceed for my Ubuntu install, so that the Windows side is happy, and I have a good Ubuntu install.

I won't be using Ubuntu all day, but I will be using it to dink around with things here and there, and of course, I plan on storing all my files on the large "Files" partition.  I will be installing the 64-bit variant.

Thanks for any and all help!

---

### Post by dabl on 2011-03-06
You're limited to 4 primary partitions.  If you use your Win 7 disk partition tool to shrink Win 7, so that you have unallocated space on the drive, then you can (using Gparted) make a fourth partition and set it as "Extended" type.  Within the extended partition you can make more logical partitions -- one for the OS and a small one for swap, for example.  Then you can install Ubuntu in that one.

---

### Post by Meetloaf13 on 2011-03-06
Perfect, I've actually already re arranged my partitions, and used gparted to delete the hidden partition.  So, I have ~44GB of free space for Ubuntu.

Should I use gparted like you said, or can I take care of that with the install?

If I remember correctly, its recommended to do 2-3x RAM for your swap?  

Should I just run the install and let it set up my partitions w/in the extended, or should I manually create things for optimal performance?

---

### Post by dabl on 2011-03-06
I personally use a Parted Magic Live USB stick that I made for the purpose.  I like to separate the partitioning task from the installing task -- makes life a little simpler, I think.

Depending on how much memory that you have, and whether you ever use suspend-to-disk (S2disk), you probably only need about 1.1X memory for swap.  Modern computers don't need to swap much, unless you are into video encoding and stuff like that.

There are things you can do with the VM system to control swapping as well (i.e. "swappiness").  Here's a link for you:

[http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

---

