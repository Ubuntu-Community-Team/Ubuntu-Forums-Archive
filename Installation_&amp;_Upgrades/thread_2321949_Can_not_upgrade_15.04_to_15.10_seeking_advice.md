---
title: "Can not upgrade 15.04 to 15.10 seeking advice"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2016-04-25
Since March we have been trying to update a laptop from Ubuntu 15.04 to 15.10 and keep getting the error "Failed to download repository information"

I was considering updating it to 16.04 however would rather wait till the next update 16.04.01 and from that time on just go with LTS updates only.

I did download the 15.10 installation but have not yet burned it to a dvd.

My questions are:

1. Would I be better off burning a dvd and installing 15.10 

a. If I did that would I be better off just overwriting the Ubuntu installation. My HDD is partitioned, so the OS resides in it's own partition.

b. Is there anything I need to be aware of if I do that.

OR

2. Would I be better off downloading the current 16.04 and installing that, overwriting the current 15.04 version that will no longer be supported by the end of this month, and just put up with any bugs etc. in the short term.

a. If I did this, is there anything I need to be aware of?

Thank You in advance for your reply.

---

### Post by kc1di on 2016-04-25
I'm not sure why your having problems with the upgrade , other than they can be problematic on some machines.  
If it were me I'd Just go ahead and to a fresh install of 16.04 , as 15.10 will only be supported until July anyway.
Back up important files first to external media.  Good Luck

---

### Post by RobGoss on 2016-04-25
I would also just do a clean install of 16.04 it might be worth it, I'm running 16.04 since Beta 2, and It's performing quite nicely.

---

### Post by grahammechanical on 2016-04-25
If you read some of the posts on this forum where users have upgraded and hit problems you will understand why some of us recommend a fresh install. The issues with upgrading come about, in my opinion, by (a) not reverting to using an open source video driver. (b) not reverting the user interface to the default state as far as possible. (c) a combination of (a) & (b).

When doing a fresh install there is always the risk of losing data. That risk is lessened if we have a separate /home partition. But we still need to know what we are doing when we use the Something Else option. If we keep all our data on a separate partition entirely then the risk of losing data is none existent. And that is why I have all my data on a separate partition.

Ubuntu 15.10 will reach end of life in the summer of this year (July). So, if you do manage to upgrade from 15.04 to 15.10 you will need to upgrade to 16.04 during August. Otherwise, you will find yourself back in the same situation you are in now. That of needing to upgrade but having to jump through hoops to do so.

Yes, it is still possible to upgrade from 15.04 to 15.10 but it is made difficult by the fact that the 15.04 software repositories are closed and have been moved to another location. Therefore, the URLs in the 15.04 sources.list file are pointing to the wrong locations. You need to edit that sources.list file and change the URLs.

It can be done. I have done it as an experiment. This explains how to do it.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

My recommendation would be to fresh install 16.04.

Regards.

---

### Post by pfeiffep on 2016-04-25
> **LaughingHorse said:**
>  ...

My questions are:

1. Would I be better off burning a dvd and installing 15.10 

a. If I did that would I be better off just overwriting the Ubuntu installation. My HDD is partitioned, so the OS resides in it's own partition.

b. Is there anything I need to be aware of if I do that.

OR

2. Would I be better off downloading the current 16.04 and installing that, overwriting the current 15.04 version that will no longer be supported by the end of this month, and just put up with any bugs etc. in the short term.

a. If I did this, is there anything I need to be aware of?

Thank You in advance for your reply.In both cases you need to take steps to back up any data, unless your /home directory is in the separate partition you mentioned. Also be aware there are many minor problems with 16.04 at this time. While they're being fixed it may take a while. If possible I suggest using a live session [either USB or DVD] to insure that the minor problems aren't major to you. I'm totally satisfied with Ubuntu Mate 16.04 and anxiously await 16.04.1

---

### Post by Bucky Ball on 2016-04-25
Fresh install. 15.04 is dead. Even if you did get to 15.10, it has a couple of months' support and you'll be doing it all again to get to 16.04 LTS.

---

### Post by LaughingHorse on 2016-04-25
Thank You all for your advice!

I was leaning to just doing a fresh 16.04 install, due to having to go thorough the process again in a few months.
the /home is separate from the data

This computer is used mainly for surfing the net, and sending email nothing really heavy.

---

### Post by RobGoss on 2016-04-25
Good luck with your install let us know how it works for you

---

### Post by LaughingHorse on 2016-04-25
Will Do

---

### Post by LaughingHorse on 2016-04-29
The install went really well, and so far everything is working.

The only issue I had on the new install was the install disc didn't recognize the root partition and data partitions, so I had to re-label them.
After that, it was the proverbial "piece of cake"!

Thank you all for your advice and assistance!

---

### Post by Bucky Ball on 2016-04-29
Great news, glad it all worked out and thanks for marking as solved. ;)

---

