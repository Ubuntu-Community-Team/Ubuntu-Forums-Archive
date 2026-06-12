---
title: "Super-mega-serious performance regression"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-10-28
I've noticed a few applications are running seriously slowly since a few days ago. 

The main one is UFRaw. To load a 12Mp raw .NEF file now takes close on a minute. If I change anything, the update takes a similar amount of time. A week ago it took less than a second.

Firefox can be sluggish at times.

Banshee has laggy moments.

Liferea can really honk on the CPU at times now.

I have a Core i7 920. It's not a slow computer. I've attached a screenshot of conky while opening a file in ufraw to illustrate the vastness of system CPU consumption.

Any ideas what's happening? Or what I could poke for better information?

---

### Post by bribera on 2009-10-28
Is this on a Karmic install? I wonder if this is an ext4-related regression. There are definite problems with applications that use sqlite (Firefox for sure, Banshee and the others perhaps).

You might try mounting your ext4 partitions with barrier=0 as described here:
[http://phoronix-test-suite.com/pipermail/trondheim-pts_phoronix-test-suite.com/2009-March/000101.html](http://phoronix-test-suite.com/pipermail/trondheim-pts_phoronix-test-suite.com/2009-March/000101.html)

However, please be aware that barrier=0 disables some write safeguards, making data loss possible in the event of an unclean shutdown.  See the section on barriers in this article:
[http://kernelnewbies.org/Ext4#head-25c0a1275a571f7332fa196d4437c38e79f39f63](http://kernelnewbies.org/Ext4#head-25c0a1275a571f7332fa196d4437c38e79f39f63)

Additional reference: [http://www.phoronix.com/forums/showthread.php?t=15877](http://www.phoronix.com/forums/showthread.php?t=15877)

---

### Post by OliW on 2009-10-28
My /home/ is actually still EXT3 (I don't trust my data to v4 yet)

---

### Post by ssam on 2009-10-28
sounds like
[http://thread.gmane.org/gmane.comp.graphics.ufraw.devel/297](http://thread.gmane.org/gmane.comp.graphics.ufraw.devel/297)

you should check if version 0.16 fixes it. if you don't want to compile, then the debain sid package will probably work [http://packages.debian.org/sid/ufraw](http://packages.debian.org/sid/ufraw)

---

