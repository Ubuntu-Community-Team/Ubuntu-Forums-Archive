---
title: "Trying to update from Feisty to Gutsy, getting &quot;FAILED TO FETCH&quot; errors !"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by VitaminBB on 2007-11-10
So this sucks ...

I havent used my ubuntu box in awhile and figured it was time I updated to gutsy from feisty, so I log in, run any updates for feisty then try to upgrade to gutsy, till now it wont work, theres no overloaded server, I think the links are just gone ...

I keep getting "failed to fetch" errors and the installation ends ...

What in the world am I supposed to do to fix this?

---

### Post by VitaminBB on 2007-11-10
Heres exactly what it says ...
> 
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_CA.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_CA.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found

---

### Post by jonnywombat on 2007-11-10
I had exactly the same problem.. I am sure there must be some sort of work around, but TBH I had a brief look on here, then gave up and did a fresh install from a live cd.

I have 3 machines of which only one updated via update manager, two failed to fetch, and then the one that did update would not install my graphics card properly and ended up doing a clean install on that system too...

My advise, save yourself the hassle and do a fresh install from a disk

Jonny

---

### Post by tubasoldier on 2007-11-10
I'm getting the same error. I would assume the Ubuntu servers are currently down for maintenance? maybe being updated?

---

### Post by VitaminBB on 2007-11-10
I dont think so, those servers are gone, as in they probably dont exist anymore and because of that im stuck ...

Someone mentioned editing the sources list, which I would try if I knew where and what to do but alas, noone seems to know ....

---

### Post by Laserbeast on 2007-11-10
Yes, those are 3rd party repos that are probably down or gone.

---

### Post by VitaminBB on 2007-11-10
So how do I fix this problem?

---

### Post by VitaminBB on 2007-11-10
Anyone have any ideas?

Its greatly appreciated and im suprised noone else has any answers, especially because with all the searchs I have done this seems to be a problem that lots of ppl are having ...

Im sure its something so deadly simple only a noob would **** it up but if some benevolent ubuntu guru could tell me what i need to do to fix this i will give them my first born child ...

Thanks :)

---

### Post by Herman on 2007-11-11
My suggestion is simply to try again later. My guess is that either the servers are down temporarily or they are busy.

Or do a fresh install from a CD like johnnywombat suggested. 
That's the way I prefer to do it myself. I never upgrade, I always install the new Ubuntu in another partition beside the older one and transfer my files across when I have tested the new install and when I'm good and ready.
Even then I keep the older installation until it's time to install the* next* new Ubuntu there in the original place. You need at least an average sized hard disk to do things this way though.

Regards, Herman. :)

---

### Post by VitaminBB on 2007-11-11
No, those servers are not coming back, they are gone, as dead as anything ...

Besides a fresh install that would destroy all I have does anyone have any clue how I can solve this problem.

I just figured someone would have an idea, apparently I have stumped everyone here and this is a problem lots of ppl were having ...

---

### Post by palmdoc on 2007-11-11
What about just editing the sources list

```
gksudo gedit /etc/apt/sources.list
```

and comment out the wine one?

---

### Post by ptn107 on 2007-11-11
1) Comment out 3rd party repositories before updating.
or
2) Backup current sources.list, delete your sources.list and use System -> Administration -> Software Sources to rebuild the sources.list; then do an update.

---

### Post by VitaminBB on 2007-11-11
Thanks ptn107,

I originally didnt know where to find the sources file and then when i found it the computer wouldnt let me change the file, it said i didnt have permission so I looked for how to change that without having to login as admin, anyway ur command line there helped a lot.

So I commented out the wine lines but medibuntu was its own list that was pissing me off so I opened it and it was empty so I deleted the ******* thing ...

This was the messiest upgrade ive ever done, why do ppl think ubuntu is ready for prime time?

---

### Post by zvacet on 2007-11-11
Before every upgrade you need to comment out any unofficial repo.After upgrade you simply add them to your sources list.  You can take from here

[http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories")

---

### Post by L9d on 2007-11-13
Try turning off those sources in your "Manage Repositories" and see if that fixes the problem.

---

