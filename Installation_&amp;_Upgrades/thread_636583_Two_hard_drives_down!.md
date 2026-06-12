---
title: "Two hard drives down!"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by rcbowser on 2007-12-10
Okay I downloaded the Xubuntu Live CD and went to install it. I have an 80 gig Seagate and a 40 gig Western Digital. When I went to do the install Xubuntu started the partition application it renamed my 40 hard drive with a bunch of ! ! ! ! ! after the name and then showed only 8gigs of space.

I spent 8 hours trying to get the 40 gigs back. No luck I then replace the 40 gig with another 40 gig harddrive. Went into windows and checked to make sure all was well. After checking the drive I again booted into Xubuntu Live CD and once again Xubuntu did the same thing!. I now have two hard drives with only 8 gigs when both should have 40. I have not a clue why this would happen.

Has anyone else experienced this?  Is there a way to fix the harddrives? :(

I would imagine there is nothing physical wrong with the drives, but I tried hard drive mechanic and software from the vendors and nothing helps.

I don't understand why Xubuntu would rename the harddrive with a number of ! !  ! !  ! after the name and how would it when all it's supposed to be doing is probing for the harddrives. 

I have ran Linux off and on for the past 3 years and never seen anything like this.
Thanks if anyone can help.

---

### Post by rcbowser on 2007-12-12
Okay I have now been able to bring the second Hard Drive back using Partitiom Magic.
For some reason gparted would not see the correct size and did nothing in the way of helping.
Using PM I was able to see the whole hard drive and discovered that the missing Gigs where still there but not partitioned. After some messing around I was  able to get the whole hard drive partitioned again to the correct size.

Still my question is why would Xubuntu change the drive when  all it's was suppose to be doing is probing for them?

Next I will try to bring the other 40 gig back up.

---

