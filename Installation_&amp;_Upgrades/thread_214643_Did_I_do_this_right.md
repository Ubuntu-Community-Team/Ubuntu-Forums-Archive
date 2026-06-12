---
title: "Did I do this right?"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by prophet11 on 2006-07-12
Ok, I installed Ubuntu from the Live CD to a 3rd HD I made the partition size 100% I slid the slider all the way to the right, so when it all installed and I started working on it, it said there was only 160MB left of space, is Ubuntu actually like 9gigs when installed or did I do something wrong? The HD is like a 9 gig HD so I was thinking of buying a 20 gig so I can install it but before I buy a new HD I was wondering if I did something wrong. If I did I would just install it on this 10gig im not really going to download much stuff I just want to play with it but I dont want to use the Live CD because I have a 10gig HD doing nothing in my computer..


Alex

---

### Post by reacocard on 2006-07-12
base ubuntu install is only 2 gigs. use System -> Administartion -> Disks to see how big your partition is. if it's too small, install gparted and resize it.

---

### Post by prophet11 on 2006-07-12
I dont have it installed anymore i took it off, i can reinstall it when i reisntall it what should i have the slider at? like 3gigs

---

### Post by reacocard on 2006-07-12
use the partition manually option, make it as big as will fit on the disk.

---

### Post by prophet11 on 2006-07-12
I did make it 100% and it filled up the HD :/

---

### Post by prophet11 on 2006-07-13
> **prophet11 said:**
> I did make it 100% and it filled up the HD :/

i dont really understand the other partitioning thing llike to pick a swap and root drives i dont want to mess something up//

---

### Post by reacocard on 2006-07-13
use gparted to delete all the partitions on that disk, then tell ubuntu to use the empty space. it will automatically set up the root and swap partitions for you.

---

### Post by prophet11 on 2006-07-13
it wants me to set a swap whatever that is to hda , hdb, or hdc then it wants me to set "/" to a,b,c then it wants me to set where it wants to install a is xp b is misc and c is the hd that i want to use.. i was just wondering why it took all the hd space when i used the other wizzard and made a partition that was 100% i guess i  am having a hard time visualing it:/ cany idagrams>

---

