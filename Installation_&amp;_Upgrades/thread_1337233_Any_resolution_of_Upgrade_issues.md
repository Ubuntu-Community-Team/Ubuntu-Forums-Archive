---
title: "Any resolution of Upgrade issues?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by henwyn on 2009-11-25
Testing Koala during development, I had a lot of problems getting it to install but was finally successful with the Beta which installed and worked without problems and which I have been using since. I have several different versions of Ubuntu and Kubuntu installed on this computer, which I have added stuff to for various purposes, and which I would like to upgrade. I tried on one of them after Koala was released and it became unbootable (an error loop on login that I can't get out of and haven't figured out how to fix yet). I know that others have reported problems with upgrading and I was wondering if these are getting worked out yet and what kind of experience I can expect if I try upgrading the other two installations on this box or my wife's or my son's computers. None of these are new hardware and all have installed and upgraded in the past without problems, but my current experience has me spooked plus what my wife will say if I mess up her computer does not bear thinking about. Thanks for any feedback.

---

### Post by jaylsi on 2009-11-25
Is the "error loop on login" like the whole screen is flickering? If that is the case, there is a sticky thread on this issue.

---

### Post by henwyn on 2009-11-25
No, I had that one earlier but fixed it. This seems like xorg,conf is probably borked. After I try to log in, it states that it cannot recognize my video card or monitor and do I want to a. retry b.shutdown or c. boot at a lower resolution so I choose a, b, or c and it goes into rinse and repeat, giving the same error message until I do a hard reset. I'll probably end up wiping and re-installing on that partition somewhere down the road. I'm more concerned if I can expect more of this on other, more crucial upgrades.

---

### Post by jaylsi on 2009-11-25
Did you try the method of removing /etc/X11/xorg.conf (by renaming) and rebooting?

---

### Post by henwyn on 2009-11-26
> **jaylsi said:**
> Did you try the method of removing /etc/X11/xorg.conf (by renaming) and rebooting?

Yes, no joy.  A lot of files are totally different between the (successful) fresh install beta and the (unsuccessful) upgrade to koala. I can do a re-install or just wipe it and wait to test Lucid on it when it becomes available. This particular upgrade is not really the problem.

My question, which I should have made more concise, was how well can I trust the upgrade process, with this distribution on a variety of older machines. The answer i get from my reading here seems to be "It depends..." and "Be ready to re-install to fix things if they get messed up." Thanks for the replies.

---

### Post by snowpine on 2009-11-26
I always recommend a fresh reinstall, based on past experience and everything I've read on these forums. (I say this even though I personally upgraded 9.04 to 9.10 no problem).

---

### Post by jaylsi on 2009-11-26
Did you ever try the 9.10 live CD?  In your case, if removing xorg.conf does not work for you, the live CD should reveal the same problem, thus saving you headache later. If live CD works, it is unlikely you will have major issues for fresh install. Upgrade from lower version can always bring problems, depending on system configuration.

---

