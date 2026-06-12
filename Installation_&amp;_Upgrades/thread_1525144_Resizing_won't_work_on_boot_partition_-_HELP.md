---
title: "Resizing won't work on boot partition - HELP"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by WinRiddance on 2010-07-06
Hi everyone. After running Lucid since it's release I decided to wipe out my Karmic partition yesterday in order to utilize that space better elsewhere. So I booted up with the Karmic LiveCD, using the option just to check out Ubuntu. Then I opened up Gparted, unswapped (unmounted) the swap partition, made sure nothing else was mounted, and proceeded to delete my Karmic partition which then provided me with about 40 GB of unused space.

Since I wanted to re-assign 10 of those GB to my primary Ubuntu software partition where I keep all of my personal data, I went ahead and resized that one to make it 10 GB larger. First I had to move the empty space over which took several hours, but that wasn't a problem. Resizing the partition wasn't a problem either. Then I wanted to re-assign the remaining 30 GB to my Ubuntu boot partition which contains strictly my Ubuntu system ... **and that's where the problem is**.

The remaining unused space on the hard disk is located directly next to my Ubuntu boot partition. No matter what I do while using Gparted via the LiveCD, it doesn't seem to be possible for me to enlarge that boot partition. Does anyone know how I can do this either via Gparted, the Disk Utility from Lucid, or even via the terminal? I'd really appreciate any help with this. Thank you.

[IMG]http://www.ubuntu.steinfein.org/diskutility.jpg[/IMG]

---

### Post by WinRiddance on 2010-07-06
BUMP ... alright gurus, I could really use some help here .... :confused:

---

### Post by efflandt on 2010-07-06
If I understand what you are trying to do, if you want to expand sda1, you first need to move up the bottom of extended partition sda2 to make room, because a primary partition cannot overlap an extended partition.

So I guess the question is whether gparted can move up the bottom of an extended partition with unallocated space at the bottom.

I would be inclined to record a snapshot of the drive with **sudo fdisk -l**, then remove everything except the first partition, create a new extended partition beginning at the same start point as Ubuntu-spare, they recreate logical partitions Ubuntu-spare and swap with the exact same start and end points they have now.

Boot Ubuntu on the hard drive and see if everything works.  If you use /dev/sda#'s instead of UUID's you may need to make /etc/fstab adjustments.  If that works, boot the live CD and expand sda1.  If not, change everything back with fdisk to the way it was before you changed it.

Removing and recreating partitions does not destroy any data, as long as they end up exactly as they were as the same type.  For example you cannot change a primary partition into a logical partition or vice versa.  But as long as a logical partition is a logical partition with same start and end points, everything should still be there, but if Ubuntu-spare is now sda6, it may end up as sda5 (and swap would end up sda6).

But just in case, it goes without saying to first back up anything on that drive that you do not want to lose.

---

### Post by drs305 on 2010-07-06
In gparted, you will see the unallocated space is inside the extended partition (light blue border). 

You will have to get the unallocated space to the far left side of the extended partition. 

Then shrink the extended partition (move the light blue border to the right), so that the unallocated space is OUTSIDE the blue box. 

Finally add the unallocated space to the Ubuntu partition.

Back up important files before doing any of this.

The second half of the first post on expanding / may be of help:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by WinRiddance on 2010-07-07
**Thanks efflandt and drs305!**

@efflandt
Your response showed me once again how little I still know. About 50% of that went right over my head and played ping pong with my feeble brain cells.

@drs305
Okay, now that I could understand a lot better because more understandable (to me) english was used in that reply. I haven't tried that but it makes sense. I'll see if Gparted will allow me to move the unused space over to the left, I'm thinking that it won't, but I'll give it a shot later on and see what happens.

__

---

### Post by WinRiddance on 2010-07-07
Bummer, seems that there's absolutely nothing that can be done via Gparted to resolve this issue of mine. Perhaps it can be accomplished via the terminal but I'm still too new to Linux/Ubuntu to dare and dive into those guts in a way where I'd be confident that nothing got messed up ... without step by step instructions that is.

**Anyway, here's what I have** ... It's a 320 GB drive that's been partitioned.

/dev/sda1 is the primary ext4 boot partition with Lucid Lynx.
/dev/sda2 is the extended partition - initially set up that way due to a WinXP setup.
(meaning due to frequent WinSystem issues, Windows was kept safely in its very own partition)

**And within the extended partition I have ....**
My unallocated space of apx. 30 GB that I wanted to move to /dev/sda1
/dev/sda5 and ext3 file system which I use for most personal files
/dev/sda6 which happens to be the Linux-Swap partition

Since the unallocated space is within the extended partition and since the partition that I wish to enlarge is located outside of the extended partition, Gparted won't allow me to do anything between the two of them. Even if I reformat the unallocated space as a ext4 partition ... it still won't let me do anything outside of the constraints of the extended partition.

**Looks to me like the only viable solution** would be to back up the data of sda1 and sda5, followed by completely reformatting the entire 320 GB disk from scratch, then setting up the partitions and sizes that I want to use ... followed by importing my backup data once that's been done. Not overly complicated, just annoying that I can't force the partitions (easily) to _work with options that permit the merging_ of the boot partition with the extended partition. Didn't think that that would be so daunting ...

---

### Post by drs305 on 2010-07-07
Gparted is a wonderful tool. Before you give up on it make sure you have met the following conditions:

1. Are running it via a LiveCD or another system rescue CD. You cannot be running it from a normal install since you won't be able to unmount your / partition.

2. Have unmounted the swap partition. Highlight the swap partition, then Partition, Swapoff.

3. Have unmounted all other partitions. There should be no "key" icons next to any of the drives. The key icon shows that a partition is mounted.

If nothing is mounted, you should be able to highlight the extended partition - it's easiest to click on the partition designation in the lower panel than trying to click precisely on the light blue border. Once highlighted and meeting the above conditions, you should be able to shrink the size either by dragging the left light blue border to the right or changing the numbers in the window that pops up when you select "Partition, Resize".

Best of luck.

---

### Post by WinRiddance on 2010-07-08
Oh, believe me, I've been around the block with Gparted and used it many times, even on Windows machines. The only way that I ever use it is via a LiveCD since that's the only way that you can unmount partitions that would otherwise be in use.

Bottom line is that you can't create operations between the boot partition and other partitions within the separate extended partition with Gparted. **My solution is to clone two of my partitions with clonezilla**. Then I'll reformat and repartition the entire disk, followed by reassigning the cloned images to the new partitions. This time I'll make sure to leave out the separate boot partition with an extended partition since this will ultimately give me complete Gparted control over the entire disk, should I need or want it later.

---

