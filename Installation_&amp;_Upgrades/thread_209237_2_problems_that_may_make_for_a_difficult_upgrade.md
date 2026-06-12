---
title: "2 problems that may make for a difficult upgrade"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by glycolized on 2006-07-04
I'm currently dual booting W2000 and Ubuntu 5.10.  I have the OSs on separate physical hard drives.

Now I just last week upgraded my video card, and I can't get Ubuntu to load X, so there's a bit of messing around there to get it going again.  I'd rather just install 6.06 fresh, as opposed to troubleshooting the video card.

Here's where my problem lies:  I'd like to put Ubuntu on a different, separate hard drive because the one I'm currently using is too small (4Gb).  Can I just pull the old HDD and install the new one, then boot with the Live CD of 6.06?  Will the grub boot loader understand what is going on, or do I risk making my Win2000 unaccessible?

Am i trying to do too much at once, meaning, should I get my existing Ubuntu running, and uninstall it, then try to start fresh?  I've had a difficult time finding documentation or removing Ubuntu from a system.

Can I make the Grub boot loader ignore the old install of Ubuntu when I install the new one?

I don't expect a full explanation, but maybe some links to articles or threads.  I've been reading threads all weekend and still am not confident that I can do this without wrecking my MBR and losing windows (which I can't have happen at this moment).

---

### Post by jmacak on 2006-07-04
Hi

I don't see why there should be a problem.  After you yank the old drive, install the new, you indicate that you then intend to boot up the live cd.  When you fire up the live cd, grub should not get involved, as long as your boot sequence looks to the cd before the fixed drives.

I doubt that the win2k will get roached.  When you install the new dapper, it should re-create the grub menu and your old dapper install should no longer show up, since the win2k is still in the same place, the grub update should still find it.

cheers

joe in seattle

---

### Post by glycolized on 2006-07-08
I'm going to give it a shot tonight.  I'll post whether it works or not (in case anyone searches and finds this thread).

---

