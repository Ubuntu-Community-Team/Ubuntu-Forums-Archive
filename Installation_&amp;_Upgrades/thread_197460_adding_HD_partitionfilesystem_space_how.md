---
title: "adding HD partition/filesystem space how??"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by herot on 2006-06-15
i have installed dapper on a 9.5 GB ext3 partition on my 80GB harddrive... i am done with windows and im not going back...  i have copied my 9.5 windows "C" drive partition to USB disk and also a 56 GB that i used to use for all my storage and programs in windows... i have also copied the entire contents of this partition "D drive" to the USB disk...

so i have an existing 9.5 GB dapper drive and a 650 MB swap partition...

i want to consolidate the old windows 9.5 GB & 56 GB partitions into the dapper file system (so i can install Neverwinter nights as i already am down to 1.5 GB on my dapper system)

whats the best way to do this??? should i leave them seperate partitions and format to ext3??? or should i delete them into free space and then expand my dapper drive???  what should i consider from performance POV???  in windows supposedly you had a relatively small "system" partition (C) and then another (or more) for program installation directorys???

advice please :) (this is my desktop not my laptop, it has a standard old IDE/ATA HD)

---

### Post by Sammi on 2006-06-15
your explaination is wayyy to confusing... so let me systemise it a little:

80 GB HDD
9.5 BG Ext3 Dapper partition
650 MB swap partition
56 GB win partition (fat32 or ntfs)
9.5 GB win partition (fat32 or ntfs)

This is how I understand your post. Please correct me if I'm wrong.

The thing I want to know is where on the harddisk these partitions are.

Because partitions can only be expanded one way with most partitioning tools - forward. And the most likely thing is that the win partitions come before the Linux ones, so it might not be possible to expand your Dapper partition to cover the whole harddisk.

---

### Post by herot on 2006-06-15
yep you got it!!

and yep linux is at the back!!!!

so keep seperate i guess and just format ext3??

partition numbers are 
hdb1 windows (ntfs)
hdb5 windows (ntfs)
hdb7 linux (/) (ext3) 
hdb6 swap

[9GB "C"] [--------------56GB "D"-------------] [9.5GB Dapper] [SWAP]

yeah... like that see!?  So... if i delete the 1 and 5 partitions... and format them ext3... can i install programs and stuff on the new partition and they work well with the dapper (hdb7) file system???  or do i need to do something special?

---

### Post by Sammi on 2006-06-15
should work fine...

---

