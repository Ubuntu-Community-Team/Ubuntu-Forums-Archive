---
title: "Partition issue. Help needed"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by flamarro on 2005-11-14
Hi,
I have a hard disk with 13G with XP (hardly used, for 6 months now :) ) and a 160Gigas one.
Ok, I used to have this last disk with a ntfs partition, but not all of it. As a newbye, i reserved some space for trying linux. i used to try mandrake, suse and for last ubuntu.
So i always had 80G to play with linux. As i was trying, i keept changing the sizes and the numbers of that partitions.
the result now is this. 70G more or less at the beginning, 2G Swap, 10G for other ubuntu, and 80G more or less ( i'm not at the machine right now ) at the end. This last one was ntfs but now is ext3 with all my junk things :) .
The initial 70G has my ubuntu that was used to try all the thing in the forums, all the instalations that i made, the upgrade from hoary to breezy, etc, and in the other partition i have a fresh install of ubuntu that is going to be the clean install, with only the things i really need.
So, what i want is, the swap partition with 2G become the first partition, the 70G one become 10G, the second ubuntu with 10G next and reserve 20G empty space to try other solution like kubuntu for ex:, and the rest become a extended partition.

I used Gparted, i reduced the 70G, but first problem i can only create primary partition, second i have a lot of data that i dont wanna miss.
Can i use the ubuntu cd, and then manage there the partitions?
What can i do wihtout loosing data? or do i have to make a clean all over install so tha i can order my partitions table?

Thanks in advance

---

### Post by az on 2005-11-14
Well, how much data is on the 70 G partition?  Can youmove it elsewhere and then shrink it down to 10 Gigs?  The delete the swap and put it after that first partitoin.  You do not need to have it as the first partition on the drive, anyway.

Then create whatever else you need with the free space.


Yes, you can do all this with parted which is on the installer.  Just let it boot up and go to the partitionner.  Then press CTRL-ALT-F2 to go to a console and run
parted /dev/hda
and do what you gotta do.

---

### Post by flamarro on 2005-11-15
ok,
As i said, i have 2 ubuntu's installed, the second one is that what i want to be clean, only with the needed things.
I started with this ubuntu, unmounted the partition with the first one and then reduced this to 10G. OK. 
Now i have a 60G free space after this 10G. The swap one i can clear it, but it is mounted as extended, and with Gparted i can only mount primary ones, as i can create only 4 primarys, i do want it to be extended as well.
Second, i can't put the second ubuntu closest to the first one, well, not with gparted, isn't that right? I can't move partitions, can i, obviously without loosing data?
The main thing here is that i want to have first, ubuntu, second ubuntu, then could have swap, no problem, then some free space and then a big extended partition with stuff.
If i can't do it, i am considering formating all and start over but now with thing more planed. Living and learning...... Thanks

---

### Post by az on 2005-11-15
You cannot move the beginning of a partition.  You can make enough free space elsewhere and copy the partition there, though.

You would have to be able to free up enough space to do that, though.

So, doing that, you can move a partition without losing data.  No problem.

---

