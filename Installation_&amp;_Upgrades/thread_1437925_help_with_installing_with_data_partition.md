---
title: "help with installing with data partition"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by wolf99 on 2010-03-24
Hi All, hoping you can discuss a few Q's I have pre install.

I have Xp Pro running (Kind of ;) ) on a desktop dual core.

I have curently only one single partition drive (C: I would like to end up with 3 partitions, 1 for XP, 1 for data and 1 for ubuntu 9.10.

What is the best way or order to go about creating the partitions? I was thinking create the data one from all the empty disk space not wanted by XP, then when installing ubuntu, it would eat up some of this data partition by creating its own (3rd) partition from that, but I am not sure if the installer works like this.

Also what would be the best format for the data partition? I have read that FAT is better for linux, but I have  large (4GB and greater) files I move about kinda regular. have read conflicting reports on how well ubuntu handles NTFS.

question the 3rd, where can I find out about ubuntu drivers for my peripherals (ie: hp w1907v screen, logitech MX laser wireless mouse, vodafone mobile broadband dongle,  etc)

Bear in mind that  I am pretty much a newb with ubuntu. Thanks for any replies, help much appreciated :D

---

### Post by mikewhatever on 2010-03-24
You can surely create a data partition and then chop some space off of it for Ubuntu. You could also chop some space off of XP and create data, Ubuntu and Ubuntu-swap partitions, either way is fine, though keep in mind that you'd have to go with manual partitioning. I'd use NTFS for the data partition.

---

### Post by coffeecat on 2010-03-24
Ubuntu handles NTFS just fine. I've used a separate NTFS data partition  for the last couple of years on several machines multi-booting Linux and  Windows. Read-write in Ubuntu is reliable. I've not had a single  problem.

You can pre-prepare all your partition in the live CD before installing,  but slightly simpler would be the following:

Boot up with the 9.10 live CD and go to System > Administration >  Gparted. Use that to shrink your Windows C:\ partition and to create a  primary NTFS partition of whatever size you want. But leave the rest of  the disc unallocated. Now close Gparted and start the installer. When it  gets to the partitioning stage, choose 'guided - use largest free  unallocated space' (or words to that effect) and it will set up Linux  root and swap partitions for you.

When you reboot into your new Ubuntu installation you will be able to  access the new NTFS data partition in the Places menu. If you want it  mounted at bootup so that an icon is permanently on the desktop, that's  easily done. Just ask if you need more information.

**Edit:** just noticed this:

> question the 3rd, where can I find out about ubuntu drivers for my  peripherals (ie: hp w1907v screen, logitech MX laser wireless mouse,  vodafone mobile broadband dongle,  etc)

You may not need extra drivers. See how your installation handles the monitor from the liveCD. If it's OK then it'll be OK once installed. Depending on your graphics card (what is it?) you may get better performance with the proprietary drivers which are easily installed from the System menu. The mobile dongle may very well just work. What model is it? Search the forum. There will be dozens of relevant threads.

---

### Post by wolf99 on 2010-03-24
hey thanks for replying so soon. I will try this.

Noob Q: liveCD = the cd I just burned with ubuntu install on it right? 

Did a quick google for my dongle, its a huwei k3765, couple of forums had threads saying kernel has problems with this???
Not overly worried about it though as its something I can sought later using my XP install

Also, I have NO graphics card (shock horror!), it s a shitty PC really, just the Mobo inside!!
this should be OK though right??

thanks again for the quick replies, means I can start tonight :D :D

Just thought, what would you recomend as a decent size partition to leave for XP?? have one or two heavy apps like Photoshop CS3, Visual  Studio 2010, solid edge, etc

---

### Post by mikewhatever on 2010-03-24
> **wolf99 said:**
> ...

Did a quick google for my dongle, its a huwei k3765, couple of forums had threads saying kernel has problems with this???
Not overly worried about it though as its something I can sought later using my XP install

Also, I have NO graphics card (shock horror!), it s a shitty PC really, just the Mobo inside!!
this should be OK though right??

You should make a live cd, run it and test all of those before installing.

> Just thought, what would you recomend as a decent size partition to leave for XP?? have one or two heavy apps like Photoshop CS3, Visual  Studio 2010, solid edge, etc

That very much depends on the size of the hdd. Make sure at least 20% of the new XP partition is free space.

---

### Post by coffeecat on 2010-03-24
> **wolf99 said:**
> Also, I have NO graphics card (shock horror!), it s a shitty PC really, just the Mobo inside!!
this should be OK though right??

Yes, but even though you don't have a separate "card" you will still have a graphics chipset on the motherboard, which comes to (nearly) the same thing. If you have problems with it, be sure to post details of what it is if you need help.

Good luck with the install.

---

