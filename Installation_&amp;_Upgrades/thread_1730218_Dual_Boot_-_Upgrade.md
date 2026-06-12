---
title: "Dual Boot - Upgrade"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by oxtus on 2011-04-15
Hi everyone,

We are getting closer to the release of 11.04. I am considering doing a dual boot (XP/Ubuntu) install when it comes out. I currently have only Ubuntu but it is getting painful to use some windows specific applications under wine.

My question are: 
Do you see any possible issues for future upgrades to 11.10?
What is your experience in the past on dual boot machines?
Tips/Method to do it painlessly?

Thanks.

---

### Post by tommcd on 2011-04-16
It is dead simple to dual boot XP and Ubuntu. 
First, install XP to whatever size partition you want for it. Leave the rest of the hard drive unallocated.
Then install Ubuntu. Choose manual partitioning. Create 3 partitions in the unallocated space: root, swap, and home. These partitions can be primary or logical. 
NOTE: You can only have up to 4 primary partitions. So make only 3 primary partitions at the most. Make the rest logical.

Root can be 10GB (or less if you are tight on space). If you have a lot of space on your hard drive, you can make root up to 20GB. For me, 10GB has been fine for the 5+ years that I have been using Ubuntu. 
Incredibly, I have seen some people around here that somehow managed to fill up a 10GB root partition. This is why I suggest up to 20GB for root. You never can tell what some people will do with FOSS software!
Swap can be 500MB-1GB if you have a lot of memory. If you plan to suspend to memory, make swap at least equal to the amount of physical memory you have.
The home partition (where your data and user specific settings live) will be the rest.

Write back if you need more help. I have been dual booting XP and Ubuntu (plus 2 or 3 other distros) for over 5 years and have never had a problem with it.

---

### Post by John Ha on 2011-04-16
Are you still around as I would like to have some advice also please, I am running Windows 7 but I also want to run Ubuntu 10.04 and I want the choice of either OS.

Thanks a million in advance.

John

---

### Post by tommcd on 2011-04-17
> **John Ha said:**
> 
 I am running Windows 7 but I also want to run Ubuntu 10.04 and I want the choice of either OS.

See these 3 excellent tutorials on dual booting Ubuntu with Windows 7 (*Graphical Installation 'A', 'B', and 'C'*) on Ubuntu forums member Herman's site here: [http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
Those tutorials are written for the current version of Ubuntu, which is 10.10, but they are useful for 10.04 also. The installation of 10.04 to dual boot with Windows 7 will be essentially the same.
Ubuntu 11.04 will be released by the end of the month, so that is another option if you want the latest (and hopefully greatest!!!) version of Ubuntu.
Here is another excellent site for getting started with Ubuntu: [http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/)
And you can get the free Ubuntu manual here:[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
Write back if you need more help. 

And welcome to the Ubuntu forums!

---

### Post by secretaznman3 on 2011-04-23
Hi,

I currently am dual booting Windows 7 and Ubuntu 10.10, and with the 11.04 release next week, I would go about just updating the 10.10 and leaving the Windows 7 partition intact.

Thanks.

---

