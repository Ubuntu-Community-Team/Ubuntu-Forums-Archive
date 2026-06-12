---
title: "Harddrive not found on install"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by Kormiku on 2007-07-22
I am trying to install Ubuntu 7.04 on my new computer, however it wont recognize my harddrive.

My computer has a core 2 duo, 250 gigabyte sata harddrive

The graphics card works, and everything boots up fine from the live cd. However, after clicking install and going through the screens it cant recognize my harddrive.

I end up at the partition screen and it tells me to manually partition my drive so I click ok. Then it sends me to the place to partition the drives and it is totally blank. There isnt anything to partition. 

I looked up some answers and found that ubuntu has a problem recognizing the bigger harddrives and that I have to change a setting in the parameters of installing it. The setting that they say to change is this: pci=nomsi

I have no clue what pci=nomsi means, but I put it into the right place and booted up my system like normal. however it had no effect and nothing changed. It still cant find my harddrive.

Do i have to mount something to get this to work? In the store when the guys were installing my harddrive, they partitioned it into two sections of 125gigabytes each. Does this have any effect on whether or not the software will install?

My computer doesnt have any previous operating systems installed. Please help out.

---

### Post by kalaspuffar on 2007-09-03
Hi

I could possibly answer that the size of the harddrive shouldn't be the issue. I just installed Ubuntu 7.04 on a 500 gb harddrive without any problem at all.

I understand that this is frustating and I can't say that I have much help to give you when it worked for me and not for you. The things i could think about right of my head is large block support in the bios but your hardware sounds pretty new so that shouldnt be an issue either. 

Maybe it's an odd manufacture of harddrives without support in the normal ubuntu install kernal. Look at hardware compabtlity pages.

---

### Post by merlinus on 2007-09-03
Try gparted l;ive cd to see if it recognizes your partitions.  

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If so, you can format them as ext3 and then see if the ubuntu cd will recognize them.

The problem may be that the ubuntu [SIZE=3]partitioner cannot use unallocated space.
[/SIZE]
-merlin

---

