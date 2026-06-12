---
title: "Partitioning - Dual Boot, Three HDD"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by Kevin_J on 2008-06-25
3 HDD: 1TB, 320GB (w/Dell restore partition), 250GB.  One will be external.

(1) where to put the common media/data partition, which will likely be NTFS?
(2) where to put the swap partition(s)?  
(3) Should Ubuntu go on the same drive as Vista, or should I give its own drive instead?  
(4) A separate partition for /home ?


I want to set up a dual-boot with Vista and Ubuntu that's going to give me the best performance (i.e. boot time, etc.) while allowing me to read my data from both Ubuntu and Vista.

My main hard drive is a nice new 1 TB Samsung - it's miles ahead of the other two in terms of performance.  I bought this because I was running out of space with the other two - I used the computer in Vista to record tv, which takes up incredible amounts of space.  

I also have a 320 GB that came with my computer, and has the restore partition which I might need if I ever need Dell tech support, so I'll have to leave that partition alone.

I have a third 250 GB western digital, about a year old, fairly fast.   

I'd like one of the three drives to function as an external hdd - I have an external cradle with an eSata connection which will give good speeds, but which also has USB to connect to my laptop.  Perhaps this is the place to store mp3s/flac files (about 120 GB) and data, I'm not sure.

So, given this, what are my best options?


I appreciate any advice, the more detailed the better.

(and yes, I've searched the forums . . . but an hour of dredging through didn't find the answers I was looking for).

---

### Post by prshah on 2008-06-25
> **Kevin_J said:**
> 3 HDD: 1TB, 320GB (w/Dell restore partition), 250GB.  One will be external.

(1) where to put the common media/data partition, which will likely be NTFS?
(2) where to put the swap partition(s)?  
(3) Should Ubuntu go on the same drive as Vista, or should I give its own drive instead?  
(4) A separate partition for /home ?




Make the 250Gb external (I'm sure that's what you'd already decided, just confirming).

Extra value suggestion: Make a partition image (using partimage) of the Dell recovery partition and burn it on a DVD for safety. For added safety, create a DVD image file (ISO) then use DVDisaster to add ECC-RS02 error correction to the DVD image before burning it on a DVD.

1) Put your common partition on the same drive as your "/home" partition (look below). This allows you a single point for backup, xfer, etc.
2) Swap on the same drive as your "/home"
3) Share your Vista drive with Ubuntu's root "/" partition.
4) Put your /home partition on a different drive from your "/" (root) partition.

Here's what I'm suggesting in more detail:

I assume that you do not want to disturb the Vista installation, which I further assume is on the 320Gb partition, in which case you'd just be adding the 1TB to your system.

So, resize your Vista partition to have about 10Gb~15Gb of free space. When installing Ubuntu, use the space for the root partition (Mount point: "/", when asked in manual partitioning during ubuntu installation). Choose type as "ext3".

Next, create another "ext3" partition, and give it between 20Gb~500Gb space for your "/home" partition; depends on how much data you want to store there.

Next create a swap partition of 1.1*RAM (eg, 2Gb RAM = 2.2 Gb swap).

Finally, create your NTFS partition for the rest of the space. (Note: you can also create an ext3 partition instead of NTFS, and give it a mount point of /extra, and then use Ext2/3 IFS extensions in Vista to read / write to this partition.)

Have none of these partitions on the external drive.

Try to avoid using extended partitions.

Having your "/home" and "/" partitions on separate drives will give a slight performance boost since both hard drives can be accessed simultaneously.

Post back if you have questions, comments or suggestions.

---

