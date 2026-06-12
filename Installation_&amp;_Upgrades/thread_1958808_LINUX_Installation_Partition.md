---
title: "LINUX Installation: Partition"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by krupas on 2012-04-14
Hi everybody. I am trying to instal Ubuntu 11.10 32bit in my Dell Inspiron N5010. I already have Windows 7 instaled in it. So the problem i am having is about the partition I am going to install Ubuntu. The thing is, i already have 3 primary partition. The first is an 100 Mb OEM Partition (i read in some forums that it is a partition for Dell software), a 16 GB Recovery Partition (witch i shrunk by 5 GB that now is not allocated so that i could install swap on it) and a 283 GB Windows OS (wich i shrunk by 20 GB that now is not allocated so that i could install ubuntu root in it). The thing is, when i start Linux installation and select one off the two unallocated partitions either for linux root or for swap, the other one become usulless and I cant do nothing with it. I googled it and i found out that there can only be 4 primary partitions and as i already have 3 i can only make one more, or for linux root, or for swap. The answer i arrived for my problem is that i have to format or OEM partition or Recovery partition. My question is wich of those two partition i should format and why. Is there another way to do this installation? For what do i use the Swap Linux Partition? Sorry for the big text and thanks for your help

---

### Post by Herman on 2012-04-14
You can use partition editing software to move the Windows partition to the left, that would give you three primary partitions followed by an area of free space, (unallocated).

Ubuntu does not need to be in a primary partition, it boots just as well from a logical partition, so you can create an 'extended' partition instead of another primary partition.
Inside the 'extended' partition you can make as many 'logical' partitions as you like, as long as they are 'contiguous', (one after the other, with no primary partition in between).

The Linux swap partition is something equivalent to what in Windows language called a 'page file', which is an area on the hard disk reserves for the system to use as a temporary storage space for memory when the motherboard's RAM modules get filled up. 
Sometimes the RAM modules don't have to be full to use the swap area, there are settings to control when the RAM is preferred and when to start using the swap area. 

Another possibility to be aware of is we don't really need a swap area in a separate partition. It's also possible to install with no swap area, (ignore the warning message), and install [Dynamic Swap Space Manager]("http://pqxx.org/development/swapspace/") instead. The operating system will run fine and Dynamic Swap Space Manager will create swap files if and when they are needed, and most of the time with modern computers now we have enough RAM so we rarely really need swap. This saves a lot of disk space, great for smaller drives like USB flash memory sticks and SSDs.
The disadvantage is the option to hibernate instead of shutting down your computer will be greyed out and you won't be able to hibernate your OS. If you want to be able to hibernate you will need a dedicated swap partition, I think twice the size of your RAM is the rule of thumb but I'm not sure.

---

### Post by krupas on 2012-04-15
Thanks for the fast answer. It was really helpfull. I was able to change the partition order with EASUS Partition Magic and i created two Logical Partitions. One with 15 GB for root and everything else and one for swap with 5 GB. Now i cant decide if i will use swap or not. I have 4 GB for RAM and the reason i would like to install swap is exactly for hybernation, but 8 GB is too much for swap partition as it will leave me with 12 GB for root and home and i will only use this swap for hybernation. So if i could Hybernate with 5 GB swap i will go with swap, if not only one partition and no swap. What do you think? I think i will install it and try. I will post what happens during my usage =D Ty again

---

### Post by D-Train on 2012-04-15
Ahhh, I guess I should have seen this thread before posting mine. My bad!

It seems my problem may be due to the fact that I already have 4 partitions. Why Dell thinks they need 4 partitions is beyond me but I may need to follow the other suggestions given here. Sorry for being such a newb.

---

