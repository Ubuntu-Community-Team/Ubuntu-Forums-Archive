---
title: "Partition space allocation for 8.10?"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by jeremywitt on 2008-11-14
So I kinda screwed up my Windows partition yesterday and I'm going to have to re-install XP... so I figured now is as good of a time as any to install the newest version of Ubuntu... 8.10.

I am going to utilize the Ultimate Gamers Edition that I've already downloaded and burned to a DVD.

I've already done all the research for installation but I want to set up 3 partitions, sharing the /home directory between XP and Ubuntu, instead of 2 partitions (1 for ubuntu and 1 for XP).

My problem is I don't know how large to make the Ubuntu Partition. Anyone know how much space to allocate for this?

---

### Post by Partyboi2 on 2008-11-16
Your /home partition is where all your data is kept so I would suggest giving this a large amount.
Not sure how big your hard drive is but for example if you had a 100 gig to use for ubuntu and a gig of ram maybe something like
/(root) 30 gig
/home 68 gig
/swap 2 gig
Really comes down to personally preference. You probably could even use 20 gig for / and put the rest towards /home.

---

### Post by nixscripter on 2008-11-16
A general rule among UNIX admins is: **swap space = real memory x 2**.

I would also suggest a separate boot partition, **/boot**, which I think is what the Ubuntu installer does by default. This should be probably be between 16 and 64 MB.

---

