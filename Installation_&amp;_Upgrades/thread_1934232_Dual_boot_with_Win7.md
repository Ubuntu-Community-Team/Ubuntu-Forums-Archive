---
title: "Dual boot with Win7"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by shvman on 2012-03-01
I would like to dual boot Ubuntu 11.10 with Windows 7. 

I've been reading several posts on this forum and the responses have helped me.  But I still have a few questions that I'd like to ask before I attempt the procedure.  

First, I have installed Ubuntu 11.10 on a laptop as the sole OS.  It was easy to do, of course, but I didn't have Windows to contend with.  

Here's my situation: 

I currently have Windows 7 installed on a desktop computer with a single hard drive.  I have a separate partition (labeled D:) for my data, making 3 total partitions (C:, system reserve, and D:).  All partitions are primary.  I have plenty of unallocated space in which to install Ubuntu.

In researching how to dual boot Win7/Ubuntu on this forum and others, I think there are at least two ways to get a dual boot system from the Live CD install options. I have a few questions about each option.

There are three install options on the Ubuntu Live CD:  one is 'install alongside Windows'.  This process appears to be automatic (or almost so).  What are the downsides, if any, of using this option?  Could I use this option even though I already have three primary partitions, or would I have to delete partition D: in order to use this procedure?  Does this option result in multiple partitions for Ubuntu?  If so, how many and which ones?  How much unallocated space does it use or does it depend upon how much space is there in the first place?

Another option that seems more configurable, and the one that I used to install Ubuntu on my laptop, is the 'something else' option.  This is almost totally manual. The upside is that you have total control over the installation process.  I assume I would define at least 3 partitions in the unallocated space on my disk: 1) /(i.e. root), 2)/home, and 3)/swap, allocating a given amount of space to each. I think I understand how to make these partitions, but I'm worried about the boot loader (Grub).  On my laptop, as I recall, I put the Grub in a separate /boot partition.  I assume I DON"T do that with Windows on the drive.  But where does it go?  One answer said to put it in "dev/sda", not a numbered partition. Is this correct?

My last question concerns the various file options.  Should ext4 be chosen for all partitions? Is ext3 a safer option?  What's the advantage of ext4 over ext3?  

None of this was made clear in the reading I've done so far.  I don't want to start the installation process without at least some guidance.

Many thanks to all for your time...

---

### Post by holycow131415 on 2012-03-01
Its best to use the disk manager in windows 7 to shrink your volume to create a new partition. Then in the livecd installer you can partition from there. with the "something else". you are only required to create a root and swap partition. Its probably good to create a home partition too if you plan on hoping around with distros. If you do the side/side in the installer, you risk breaking windows. Go with ext 4, its faster and yes its stable and the default.

With grub, just go with the default selection.

---

### Post by darkod on 2012-03-01
The auto option (along side windows) will create a root and swap partitions only. Their size will automatically be decided by the installer according to the free space it has for ubuntu. You have no control over it. It will use all the free unallocated space but it will never touch any of your other partitions.
You can use this options if you already have 3 primary partitions (system reserved, C: and D: ). But you also might have a restore partition which is hidden and primary. In that case you can't use any method, auto or manual, until one primary is deleted.
Make sure you only have the 3 primary partitions you specified.

The manual option gives you total control, as you already said. I always recommend it. Not only you have total control over partitions sizes, but also you can select where the bootloader gets installed which is especially important with multiple disks (you have only one).
Also, the manual option allows you to install with separate /home partition like you plan, which is very good to have for future clean installs.
The filesystem for / and /home is usually ext4, for swap it's simply swap area (in case you don't know, swap doesn't use mount point, when setting it up don't be confused).
The bootloader grub2 should go to a MBR of a disk, which means WITHOUT any number, just /dev/sda, /dev/sdb, etc.

---

### Post by shvman on 2012-03-04
Thank you very much.  This helps a lot!

---

### Post by Mark Phelps on 2012-03-04
The alongside option will shrink the Win7 OS partition using a Linux filesystem utility -- which has left some Win7 machines unbootable as the Win7 filesystem got corrupted in the process.

To be safe, you should only use Win7 to shrink Win7 OS partitions.

---

### Post by darkod on 2012-03-04
> **Mark Phelps said:**
> The alongside option will shrink the Win7 OS partition using a Linux filesystem utility -- which has left some Win7 machines unbootable as the Win7 filesystem got corrupted in the process.

To be safe, you should only use Win7 to shrink Win7 OS partitions.

Mark, since I don't use much the auto methods, what does the menu look like these days (in ubuntu 11.10 for example) if you have unallocated space to use?

The OP has this situation exactly. There is unallocated space to use, so there is no need for shrinking.

Earlier, when you had unallocated space, the partitioning step looked like:
- install side by side (using the slider thing)
- use largest continuous free space
- erase and use whole disk
- manual partitioning

Since then, they have renamed manual into Something Else (much more confusing than Manual).
I believe also that for installing into unallocated space now you need to select "side by side" and you will be presented with a sub-menu in the next step, whether to use the slider and shrink, or use the unallocated space.
Do you have experience how this works now? How would one install into unallocated space without resizing any partitions?

---

### Post by shvman on 2012-03-12
> **Mark Phelps said:**
> The alongside option will shrink the Win7 OS partition using a Linux filesystem utility -- which has left some Win7 machines unbootable as the Win7 filesystem got corrupted in the process.

To be safe, you should only use Win7 to shrink Win7 OS partitions.


Many thanks fellows.  I'll let Windows make a partition for me and install  via "manual".

John Stewart

---

### Post by Mark Phelps on 2012-03-13
> **darkod said:**
> Mark, since I don't use much the auto methods, what does the menu look like these days (in ubuntu 11.10 for example) if you have unallocated space to use?...

Sorry, missed this thread and never got back ...

But, I don't install Ubuntu to any drives that share Windows OSs.  Always install Ubuntu to its own drive.  So, don't really have experience with different "shrinking" scenarios involving Windows filesystem partitions.

---

