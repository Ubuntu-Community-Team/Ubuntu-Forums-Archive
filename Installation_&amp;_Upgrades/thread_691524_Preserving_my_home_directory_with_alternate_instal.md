---
title: "Preserving my home directory with alternate install disc"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by sbilstein on 2008-02-08
I have quite a problem.
I recompiled my kernel on Gutsy 7.10 to an older kernel so that I could get my laptop to sleep and hibernate using slab rather than slub.
That worked fine. Except my ati card wasn't exactly pretty. However when I attempted to reinstall my drivers things got really bad and X broke and so did everything. I managed to recover to the point where I can use default crappy drivers but my compiz doesnt work and I have to manually run metacity when I boot.
Essentially, my install is a mess right now.
I want a fresh start; problem is my home directory is on the same partition as my /. I read here [https://wiki.ubuntu.com/UbiquityPreserveHome](https://wiki.ubuntu.com/UbiquityPreserveHome) that it is possible with 8.04 but it also mentions that using an alternate install disk it is possible.

I'd like to downgrade to 7.04(it does what I want apparently). The ubuntu site vaguely mentions deleting everything manually except for the home folder and installing the OS over that. I have no problems doing that. I have no real way of backing up my home (its about 60 gigs of not easily recovered music). Any idea on how to do this?

---

### Post by kidders on 2008-02-10
Hi there,

I'm very dubious about the idea on the other end of that link you posted. Installing Linux without formatting the underlying filesystem would make me quite uncomfortable.

Since you should probably have a backup of your personal files anyway, I would suggest making one ... even if you wind up having to burn them onto a bunch of DVDs. From there, you could repartition your hard disk, and restore your /home to a partition of its own & downgrade Ubuntu.

Whatever you choose to do though, be it on-the-fly filesystem resizing or some other variant on the above, I can't say I would recommend doing anything that involves reinstalling an OS or tinkering with partition tables without a good quality backup of any data you can't afford to lose.

---

