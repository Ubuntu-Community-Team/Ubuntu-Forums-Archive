---
title: "Can you remove a windows partition and slide the ubuntu to the start?"
date: 2016-11-01
forum: Installation &amp; Upgrades
---

### Post by coppyhop on 2016-11-01
I want to remove a windows partition and go full ubuntu. Problem is the Windows partition is before the ubuntu partition. Would it be possible to slide the Ubuntu partition backwards to the start of the drive?

---

### Post by Bashing-om on 2016-11-01
coppyhopl Hey .

Sure it is doable ! But, It does have it's risks as you are also moving the partition table - bad things can happen.
Back up your data and be prepared to RE_install afresh .

[INDENT][INDENT]life in the fast lane
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2016-11-02
Yea. Pretty easy, but you may have issues with boot after. Fixing that should also be straightforward.

As Bashing-Om says, back up before doing resizing whenever you do it, now or in the future.

Boot to a 'live' session (Try Ubuntu from the install media)> once at a desktop launch Gparted> right click the paritions you are going to resize and make sure they are unmounted> right click on the Win partition and delete it> right click on the Ubuntu partition and resize into the empty space, be it at the beginning or the end.

You'll find you can move the slider in to whichever end of the partition there is free space. Good luck.

---

### Post by yancek on 2016-11-02
If you already have Ubuntu installed and windows in front of it, you could save yourself a lot of trouble by simply formatting the windows partition from Ubuntu with a Linux filesystem to use, create a mount point for it and an entry in /etc/fstab and use it for data.  If you don't want that, the suggestions above should work but moving all the boot files can create an unbootable machine if you are not careful.

---

### Post by kevdog on 2016-11-02
Am I wrong -- I definitely could be - however I thought you couldn't resize partitions other than the last one, unless you started deleting partitions to get to others.  Is this logic totally incorrect?

---

### Post by Bucky Ball on 2016-11-02
> **kevdog said:**
> Is this logic totally incorrect?

Not sure, but I'll take a punt. If you want to resize sda5, say, you need to *unmount* anything below it, sda1 and 2 for instance, not delete them. :)

If you boot to a live session, unmount all partitions, knock yourself out! Resize as you wish without deleting anything. You will possibly need to spend a bit of time getting things booting after the enterprise, though. :)

---

### Post by yancek on 2016-11-02
> Am I wrong -- I definitely could be - however I thought you couldn't  resize partitions other than the last one, unless you started deleting  partitions to get to others.  Is this logic totally incorrect? 		

You can resize any partition anywhere on the disk depending upon the circumstances.  If you want to shrink a partition, you must do it from outside the partition.  Usually a Live CD is used and the partition must be unmounted.  If you want to increase the size, you would need unallocated space and if you have that available contiguous to the partition, that works.  The partition you want to increase the size of must also be unmounted.  You would need unallocated space after/before the last partition too or you would need to create it by deleting a partition.

> Not sure, but I'll take a punt. If you want to resize sda5, say, you need to *unmount* anything below it, sda1 and 2 for instance, not delete them.

I don't think so although that might be the case with GPT?  On a standard MBR with an Extended partition, only the extended and logical need to be unmounted and that is only the partition(s) which will be affected.  A problem I see a lot with this is that if you delete a logical partition, any partition with a higher number will be changed to a lower number.  If you have sda5 (always a logical on MBR) and sda6 and delete sda5, the previous sda6 will change to sda5.

---

### Post by Bucky Ball on 2016-11-02
An  extended partition is seen by the system as one partition (in a legacy/BIOS install it is counted as one partition, regardless of how many logical partitions you might have in there). To unmount an extended partition you need to unmount *all* the logical partitions within it. :)

---

### Post by kevdog on 2016-11-03
Thanks guys for the information -- makes sense.  I converted to GPT based partitions a long time ago -- in fact its pretty easy to convert from a standard MBR to a GPT type partition table from a live CD.  I know everything can be done on the command line, however a tool like Gparted does make it very easy to shrink and expand and create partitions.

---

