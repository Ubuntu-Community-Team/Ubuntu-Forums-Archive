---
title: "Installation questions"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by TokyoTragic on 2010-05-20
I uploaded pictures to my photobucket to go along with my problem. Sorry for the quality. Anyway My problem is I'm trying to install ubuntu to my laptop. That's not the problem. The problem is that my hard drive is split into two drives(c and d drives) when I try to install ubuntu instead of ubuntu installing on the empty drive it tries to split the memory on my primary drive instead of installing the backup drive. I need to know what I need to do to either delete the d drive so i can install ubuntu and split the memory between the two os, the proper way to get ubuntu to install ont he d drive, or whatever way you guys suggest that will solve my dilemma.

Here are the pictures
[http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00028-20100520-1706.jpg](http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00028-20100520-1706.jpg)
[http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00029-20100520-1707.jpg](http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00029-20100520-1707.jpg)
[http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00030-20100520-1708.jpg](http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00030-20100520-1708.jpg)
[http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00031-20100520-1708.jpg](http://i567.photobucket.com/albums/ss115/OfficialZer0/Computer/IMG00031-20100520-1708.jpg)

---

### Post by darkod on 2010-05-20
First of all, for clarity, if you have only one single physical disk, then C: and D: are partitions, not drives. Yes, I know, windows calls them drives. :)

If you created the D: partition from windows, it is probably formatted as ntfs. Linux doesn't install on ntfs, it has its own filesystem (these days ext4, earlier ext3, but there are others too).

If you want to install ubuntu in the place of the D: partition, the best is: boot windows and delete the D: partition. Leave the space as unallocated, do NOT create any other partition in it.

Boot with the ubuntu cd and start the install process. In step 4, when asked, tell the installer to install with the Use Largest Available Free space option. That will install ubuntu into the unallocated space you left.

It needs to have unallocated free space, not belonging to any partition, so it can create the partitions for ubuntu. Existing partitions, especially ntfs, don't count even if they have "free" unused space. That's the problem at the moment.

If you have any questions, just ask.

---

### Post by TokyoTragic on 2010-05-20
> **darkod said:**
> First of all, for clarity, if you have only one single physical disk, then C: and D: are partitions, not drives. Yes, I know, windows calls them drives. :)

If you created the D: partition from windows, it is probably formatted as ntfs. Linux doesn't install on ntfs, it has its own filesystem (these days ext4, earlier ext3, but there are others too).

If you want to install ubuntu in the place of the D: partition, the best is: boot windows and delete the D: partition. Leave the space as unallocated, do NOT create any other partition in it.

Boot with the ubuntu cd and start the install process. In step 4, when asked, tell the installer to install with the Use Largest Available Free space option. That will install ubuntu into the unallocated space you left.

It needs to have unallocated free space, not belonging to any partition, so it can create the partitions for ubuntu. Existing partitions, especially ntfs, don't count even if they have "free" unused space. That's the problem at the moment.

If you have any questions, just ask.

Ok I just right clicked on my computer, clicked manage, went to storage, disk management and deleted my d drive. It now says free space instead of d drive. If this works I will love you forever! :p haha. wish me luck

---

### Post by darkod on 2010-05-20
Be careful, the second partition on those screenshots looks like a logical one. Logical partitions reside inside extended partition, which is still a partition.

If you deleted just the logical partition, the free space is still not unallocated but it is free space inside the extended partition. Delete the extended too.

I think Disk Management should mark it with black color when it's unallocated. Blue is for primary partitions, and green for extended.

---

### Post by TokyoTragic on 2010-05-20
I was able to install ubuntu... Thank you!

---

### Post by TokyoTragic on 2010-05-20
<<< has no idea how to close this thread... but seriously thank you! Now going back to ubuntu to get all the updates and get set up. Thank you again darkod

---

### Post by darkod on 2010-05-21
> **TokyoTragic said:**
> <<< has no idea how to close this thread... but seriously thank you! Now going back to ubuntu to get all the updates and get set up. Thank you again darkod

No problem.

For marking as Solved, you need to be logged in and look above the first post in Thread Tools. You can mark it as solved there.

---

