---
title: "Partition Question"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by bethaviv on 2007-11-04
Ok... I spent about an hour looking for a more "English" answer to a question before I just partition my drives like I always do ( /, /home, swap) since that is what most guides say to do.

I've heard that splitting up an install with many partitions will make Linux run faster or more efficient (not sure if this is a true statement, but just what I've been told) and I do have 200GB to spend on my install. Normally I just make a 10GB /, 2GB swap and the rest for /home. I was looking at forums and Google to find a clear explanation on setting up the other type of partitions, but I honestly had trouble following the details.

Example: /boot has to be installed on the first 1024 cylinders. How many MB/GB are in the first 1024 cylinders? I haven't a clue.

I guess I just want a more "personalized" and layman-terms explanation. Where the partitions should be mounted and if they need to be primary or logical. And maybe a recommended size for each. I plan to be playing around with Wine, C-F and AWN... Just learning Linux more.

Thanks =D

---

### Post by rsambuca on 2007-11-04
I honestly believe there is absolutely no reason to split up your system into a number of different partitions for regular desktop use.  There is simply no point to it, and it will inevitably just end up wasting harddrive space.

In the old days, it was recommended that for quickest access, the swap partition be put in the first sectors of the drive as access times were quicker.  Frankly, most people don't even use the swap now, and speed times have overall increased, so it really isn't that big a deal.

I would stick with /, /swap, and either a separate /home or /media partition.

---

### Post by bethaviv on 2007-11-04
Would you have a good website to go to so I could read up more on the different partitions and how they're used?

I've been to a couple already, but, like a mentioned, they didn't give a whole lot of info.

---

### Post by rsambuca on 2007-11-04
I'm not sure what kind of info you are specifically looking for, but here are a couple:

[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by bethaviv on 2007-11-04
The freeOS site is a lot more detailed than the other sites I've been to, thank you =)

I'll read up a bit and see if any of the other partitions are useful to me.

---

### Post by rsambuca on 2007-11-04
There really is no need to separate the different directories into their own partitions.  It won't make your system run any faster, unless they are all on separate physical drives.  If anything, it will make it run slower since the head will have to be traveling all over the platter to the different partitions.  I would urge you to reconsider.

---

### Post by bethaviv on 2007-11-04
I'm not one to go running blindly into something.. that's why I wanted more info =)

I maybe new to Linux, but not to computers =D

And I think HDDs are fast enough that I wouldn't notice a slow down even if I created a partition for all the Ubuntu options. I have 2  Raptor X drives (RAID0 w/ Vista) and I've seen the head going back and forth, I honestly don't believe there would be a noticeable slowdown (the head moves at the same speed as a 7200RPM drive, the platters just spin faster in the 10K RPM drives).

But anyway...

I have decided to make a /boot because I will probably put SuSe on my OS HDD (the Admins use SuSe at work and I would like to be able to help). I read that a /boot is good if you're going to be installing multiple distros and it prevents some issues with GRUB when installing other distros.

---

### Post by rsambuca on 2007-11-04
> **bethaviv said:**
> I'm not one to go running blindly into something.. that's why I wanted more info =)

I maybe new to Linux, but not to computers =D

And I think HDDs are fast enough that I wouldn't notice a slow down even if I created a partition for all the Ubuntu options. I have 2  Raptor X drives (RAID0 w/ Vista) and I've seen the head going back and forth, I honestly don't believe there would be a noticeable slowdown (the head moves at the same speed as a 7200RPM drive, the platters just spin faster in the 10K RPM drives).

But anyway...

I have decided to make a /boot because I will probably put SuSe on my OS HDD (the Admins use SuSe at work and I would like to be able to help). I read that a /boot is good if you're going to be installing multiple distros and it prevents some issues with GRUB when installing other distros.

I have XP, Vista, and 5 linux distros booting from grub, and I don't have a separate /boot.  A separate /boot can come in handy if you are using external drives that aren't always connected, though.  You are obviously free to do what you wish (the true beauty of linux), but I see no reason to make things more complex just because you can.

---

