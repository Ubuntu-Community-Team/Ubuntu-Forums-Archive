---
title: "M1330 Dual Boot and Media Direct"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by agentnixon on 2008-03-05
Hi, I've heard wonders about linux and want to give it a try, but I don't want to completely stray away from Vista... yet. I would consider my computer skills to be average. 

So the thing is: I want to dual boot both Vista and Ubuntu (the Dell version from their website). The problem is, there is already 4 partition sections, and that is apparently the maximum, therefore, I need to get rid of 2(or 3?) sections. 

I've already deleted the Recovery partition, so now I have 3 left: the Vista, the Dell Utility, and the Media Direct. 

My question is:
a) how many partitions does ubuntu require? 2 or 3?
b) how do I remove Media Direct partition without harming Vista (ie not wiping the drive clean)
c)is the Dell Utility partition nessesary? And does it need to be removed to install Ubuntu anyways? 

Many thanks, 
Agent Nixon

---

### Post by petzworld999 on 2008-03-05
Ubuntu needs 1 partition to install. There is a utility in the installer from the live cd that will help you through the partitioning process. I would give Ubuntu about 12 gigs to start, and that can always be expanded. You don't need the Media Direct partition, and the Dell Utility partition, I believe, is much like a recovery partition; filled with useless junk you will only need if you really screw up your machine. Ubuntu will not mess your machine up.

---

### Post by agentnixon on 2008-03-05
I've tried installing with only the (used to be) Recovery partition, but it gives me a error saying that there is not enough partitions. That is why I am inquiring about the Media Direct partition.
Unless of course, there is a solution to this error. I vaguely remember it saying something like "there is an error. It is usually because there is not enough partitions" or something along that line.
Thanks.

---

### Post by petzworld999 on 2008-03-05
Make sure you format what used to be the recovery partition as ext3. If the recovery partition was fairly small, you will probably need to format the Media Direct partition and recovery partition as one ext3 partition. You should not need more than 1 partition.

---

### Post by agentnixon on 2008-03-05
Alright, thanks. I will try to expand my Recovery to 15GB (taking 5 from my Vista). I'll report back if I have any issues.

---

