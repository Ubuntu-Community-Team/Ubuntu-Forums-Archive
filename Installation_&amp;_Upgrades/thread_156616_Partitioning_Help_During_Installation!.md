---
title: "Partitioning Help During Installation!"
date: 2006-04-07
forum: Installation &amp; Upgrades
---

### Post by michaelzhao on 2006-04-07
Here's the problem guys. I want to install Ubuntu with a dual boot... its going to place nice with Windows Media Center Edition. I have 3 HD's. Two are Western Digital 74 gig raptors in Raid. The third is a Western Digital 400 gig deep storage drive.

I initially wanted to install linux on the deep storage drive. But alas! When I was formatting that in  Windows... I accidentally made a Dynamic partition and not a basic partition. So I'm forced to install Linux on my raptors.

So I get Partition Magic from the wide expanse of the Internet. Run it, and decide to partition my raptors. Now, I have MCE booting from my raptors. I decide to partition 15 gigs for Linux using the Ext3 file system and another 2 gigs for the Linux swap file. 

Now.... when i was finishing this up. Partition Magic asked me if I wanted to make this an active partition. Now... I said because I had one active partition on my C drive, Windows I didn't want to complicate matters and make my new Linux partition a active partition as well. 

So I popped in the Ubuntu install CD... compliments of ShipIt and Canonical... and decide to give Linux a whirl. So when it gets the partitioning section of the install... its not finding the partitions I made on the C drive. 

Here's my question. During the partitioning done by Partition Magic, should I have made the ext3 file system partition an active partition? Or should I have used FAT32 and waited for Ubuntu to format the FAT32 into the EXT3 file system?

C'mon Linux Gods/Gurus/1337sters.... help me with this!

---

### Post by bscbrit on 2006-04-07
If you left the partitions unformatted then Ubuntu usually gives you the option of using 'Unused Space' or something similar.

Having selected the new partitions using PM, did you remember to press the button that actually carries out the repartitioning task?  I know that I have forgotten this in the past!

I don't think that your problem is anything to do with selecting or not selecting the partition as active.

However, I am also aware of some people experiencing problems with partioners which are run under windows when the partition is subsequently used by linux - you might be one of the unlucky ones.  it is something to do with the way that the partition boundaries are written to disk, but to be honest I cannot remember the details.

---

