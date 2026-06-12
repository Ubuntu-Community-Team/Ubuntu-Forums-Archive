---
title: "Can I keep my dual-boot as it is while reformatting my Ubuntu partition for Karmic?"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by space-litter on 2009-10-06
I would like to benefit from the ext4 and GRUB updates that come with Karmic. As it stands I am currently dual-booting into Vista and Jaunty. From what I have read, simply updating through Synaptic will not provide what I am looking for. Is it possible to simply "overwrite" the Jaunty partition with a Karmic liveCD, keep my current partitions as they are, and still get the ext4 and GRUB benefits? Or would this require a complete reformat?

I am fine with backing up my Jaunty files to replace once the Karmic install is complete, but if I would have to reformat the entire hard drive and reinstall a new Vista partition as well...I would have to think twice.

---

### Post by wilee-nilee on 2009-10-06
If I under stand you correctly you want to replace Jaunty with Karmic. If this is the case just finish the back up then delete the Jaunty and swap partitions with gparted in the live Karmic or a live jaunty cd leaving the partition with a blank area. Then write down the size of the windows partition, so when you get to the partition Gui in the Karmic install choose side by side and adjust the slider on the bottom to hold the windows in it's original partition size and keep on going. The only thing I will say as well is that people are having problems with wireless right now so be sure that if you need wireless you may not have it. I used a older daily Karmic live CD and changed to wicd before updating to bypass this problem. I also just for kicks downloaded todays daily build of Karmic and it was using the wireless like normal without the install and the little spinning icon looked different so maybe things are getting worked out. 

The Gui partitioning choice in the Karmic may be actually install in the largest open space, what your looking for is that slider that will adjust the partitions to how you want them.

---

### Post by space-litter on 2009-10-06
Yes, normally I would just do a normal distro update through Ubuntu itself. But since I want the new GRUB and ext4 filing I read it would have to be a fresh install. I just don't want to have to reinstall Vista in the process.

So, as long as I tell the partition GUI to keep the sizes exactly as they are during the Karmic install, it will not accidentally overwrite ANY of the Windows partition?

And thank you for the tip; I will probably wait until the final release at the end of the month but wanted to start preparing now in case I did have to back up Vista as well. It has multiple user accounts on it and would be very time consuming.

---

### Post by wilee-nilee on 2009-10-06
> **space-litter said:**
> Yes, normally I would just do a normal distro update through Ubuntu itself. But since I want the new GRUB and ext4 filing I read it would have to be a fresh install. I just don't want to have to reinstall Vista in the process.

So, as long as I tell the partition GUI to keep the sizes exactly as they are during the Karmic install, it will not accidentally overwrite ANY of the Windows partition?

And thank you for the tip; I will probably wait until the final release at the end of the month but wanted to start preparing now in case I did have to back up Vista as well. It has multiple user accounts on it and would be very time consuming.

 The install will give you the option of overwriting the whole HD so just carefuly read on the install and be sure to defrag windows before you do anything.  Hopefully others will chime in with confirmation but the method I described is the way that works best for me. I have seen people advise to set up the new Linux partition but the install disc as far as I know will over write that so a blank partition space seems prudent.  So when you finally install run sudo update-grub this will have the new grub recognize the vista partition.

---

