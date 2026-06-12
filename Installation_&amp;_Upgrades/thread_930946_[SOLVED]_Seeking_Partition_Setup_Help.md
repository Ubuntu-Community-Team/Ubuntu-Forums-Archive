---
title: "[SOLVED] Seeking Partition Setup Help"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by Henuboat on 2008-09-26
I seem to have gotten myself in quite a mess...

I currently have a single HDD, 160 GB in size.  XP is installed and Ubuntu was also, but I was having so many issues I deleted Ubuntu's partitions inside XP (and at the same time messed up Grub, so I can't boot back into Windows, oops.)

I want to repartition the free space and install Ubuntu on it, however the easy guided options seem confusing (I think they want to put Ubuntu on the same partition as windows, instead of creating a new partition for it).  I would like to set things up in the Manual option but I don't know what to create.  

Here is what it says at the moment:

/dev/sda
/dev/sda1   ntfs  size:94582MB used: 19600MB
free space            size:65415MB

I would be most grateful for instructions about what kind of partitions to create and what settings to use.  Thank you for any help.

---

### Post by Sef on 2008-09-26
>  I would like to set things up in the Manual option but I don't know what to create.  

Here is what it says at the moment:

/dev/sda
/dev/sda1   ntfs  size:94582MB used: 19600MB
free space            size:65415MB

I would be most grateful for instructions about what kind of partitions to create and what settings to use. Thank you for any help.Highlight  'free space            size:65415MB', then set up partition > make it an extended partition instead of a primary.  (You have only 4 primary partitions, but as many extended ones as you like.)

Once that is done, go back into the ended partition, and make it 8 - 10 GB.  The default file system is ext3, keep that and set up the partition as / (root.)  

Second, go back into  'free space            size:65415MB' > set to 1 GB > at file system > change to swap > go back to free space.

Third, go back into ' free space            size:65415MB' > set up the rest as ntfs or ext3 > set the partition up as home.   Ubuntu has 3g-ntfs which can read ntfs.  Windows will need software to read ext3.  Most people go with ntfs set up.

Last format the new partitions.

To read about manually partitioning, see the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by Henuboat on 2008-10-03
Thank you very much Sef for your help!

For other people with the same problem that might find this thread:

I am using a 8.04 install disk I burned last week.

> **Sef said:**
> Highlight  'free space            size:65415MB', then set up partition > make it an extended partition instead of a primary.  (You have only 4 primary partitions, but as many extended ones as you like.)

Once that is done, go back into the ended partition, and make it 8 - 10 GB.  The default file system is ext3, keep that and set up the partition as / (root.)  

I tried creating one large partition but then I could not resize it using the "Edit Partition" button. So I deleted it and then created a partition as follows (leaving as default what Sef did not specify:)

Logical
10,000MB in size
Beginning
Format: EXT3
/

> **Sef said:**
> Second, go back into  'free space            size:65415MB' > set to 1 GB > at file system > change to swap > go back to free space.

Logical
1000MB in size
Beginning
Format: Swap

> **Sef said:**
> Third, go back into ' free space            size:65415MB' > set up the rest as ntfs or ext3 > set the partition up as home.   Ubuntu has 3g-ntfs which can read ntfs.  Windows will need software to read ext3.  Most people go with ntfs set up.

NTFS was not an option (the options were: Ext3, Ext2, ReiserFS, JFS, XFS, Fat16, Fat32, Swap and EFI).  So I went with EXT3.

Logical
(remaining space in size)
Beginning
EXT3
/home

> **Sef said:**
> Last format the new partitions.

I checked off "Format" for the first and third partitions, it would not let me format the Swap partition.

The install seems to have gone well, I can login. It didn't pick up my network settings but that's for another thread :)

Thanks again Sef!

---

