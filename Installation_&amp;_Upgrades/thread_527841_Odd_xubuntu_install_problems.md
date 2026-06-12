---
title: "Odd xubuntu install problems"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Freakazoid10 on 2007-08-17
been trying to install xubuntu on a thinkpad 600x that currently has 192Meg of ram. (also it's a p3-m 500mhz)
Well, the alternate install fails in interesting and strange ways. The last way it failed was asking for the 7.04 install cd, that was a wtf? moment as that was the cd that's in the freaking drive.
So I tried the "desktop" install CD. That one behaves well (if slow starting) until it gets to actually installing things, then everything just dies. Check memory and sure enough: hardly anything left.
Ran into this and decided to try it. (makes sense, give it some swap)
[http://cutecomputer.wordpress.com/2006/07/18/ubuntu-606-installation-on-legacy-pc-low-ram/](http://cutecomputer.wordpress.com/2006/07/18/ubuntu-606-installation-on-legacy-pc-low-ram/)
well, the problem with that is that mkswap runs fine but when I run swapon it always complains that the partition is busy.


anyone have any ideas? i'm out.

---

### Post by K.Mandla on 2007-08-17
Sometimes on slower or older computers the CDROM takes a few seconds to respond. I've seen one or two where there was a delay in hardware acknowledgement, which looks like an error, but it really just needs a few more seconds to reply.

Try the alternate install again, and this time, when it asks for the CD, try repeating that step. It might find the drive on the second try.

As far as the desktop install, 192Mb is pushing the limit for free space. You might have to rely on the alternate install CD to get something working.

---

### Post by Freakazoid10 on 2007-08-17
Did just that last night after I posted that. For some strange reason it worked fine, despite failing miserably other three times. (it really failed four times but the first didn't count as I had a bad burn) Currently doing a through scan of the hard drive right now as it's a hand me down from a friend. (6 gig wasn't enough, he had a 40 lying around) 
finished installing then I started that off, it's still running. has around 3 1/2 hours left

---

