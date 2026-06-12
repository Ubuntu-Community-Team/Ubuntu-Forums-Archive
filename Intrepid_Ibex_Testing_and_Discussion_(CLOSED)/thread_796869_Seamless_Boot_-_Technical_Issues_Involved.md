---
title: "Seamless Boot - Technical Issues Involved"
date: 2008-05-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by CrazyGuy123 on 2008-05-16
I  am particularly interested in knowing if it is possible to initialize a graphics card from VESA mode (as it may be in from usplash or the BIOS logo), to a composited desktop, without a single blank frame (ie. no flicker).

1.  Is there hardware spport for this, or do graphics cards require re-initialisation to switch out of VESA?  If they require reinitilisation, is there any chance of completing it inside the vertical refresh period so it is still flicker free?

2.  How many software changes would be required?  Obviously X would probably need big changes (it needs to start without touching the display till the last minute when it's actually got a picture to show).  Graphics drivers also presumably need big changes, and probably changes to usplash and the boot sequence to handle handover gracefully.

---

### Post by quickshade on 2008-05-16
This is already planned for kernel 2.6.27. Which should be out this fall, BUT you are right, most hardware won't support the mode out of the box (Intel likely the only one) and X needs some reconfiguring. If anything, Look for next spring for that feature to have a chance.

---

### Post by CrazyGuy123 on 2008-05-16
hi do you have any more info on that or links quickshade?  Is it implemented through "freezing" the video image during a mode change (like the OLPC XO-1 does by having effectively two graphics devices that can drive the screen), or by entirely avoiding the mode change (a better solution in the long term IMO, although probably harder to implement)

---

### Post by aamukahvi on 2008-05-16
> **CrazyGuy123 said:**
> hi do you have any more info on that or links quickshade?  Is it implemented through "freezing" the video image during a mode change (like the OLPC XO-1 does by having effectively two graphics devices that can drive the screen), or by entirely avoiding the mode change (a better solution in the long term IMO, although probably harder to implement)
Check this out
[http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1](http://www.phoronix.com/scan.php?page=article&item=kernel_modesetting&num=1)

---

### Post by gnomeuser on 2008-05-17
As usual the Fedora Project is doing the required work, in F9 we shipped an early preview of the kernel modesetting technology for the intel cards. The aim is to have this working full for F10 as part of the Flickerfree boot project.

F10 first progress to show we are making this happen:
[https://www.redhat.com/archives/fedora-devel-list/2008-May/msg00954.html](https://www.redhat.com/archives/fedora-devel-list/2008-May/msg00954.html)

Feature tracking:
[http://fedoraproject.org/wiki/Releases/FeatureBetterStartup](http://fedoraproject.org/wiki/Releases/FeatureBetterStartup)

So if you want this, come help us build it.. The plan is clear and we have 6 months to make it happen so all hands on deck would be nice.

---

### Post by CrazyGuy123 on 2008-05-19
Cool thx for the info.

I would offer to help out, but I'm afraid I don't think I have enough knowledge of fedora or graphics hardware to be much help.

---

### Post by gnomeuser on 2008-05-19
> **CrazyGuy123 said:**
> Cool thx for the info.

I would offer to help out, but I'm afraid I don't think I have enough knowledge of fedora or graphics hardware to be much help.

we need testers, hammer on the code file bugs.. that alone would further us quite a bit. Currently I would not recommend installing our development branch it just opened so the influx of new features are still settling down. In about 2 months we are shipping our alpha release at which point we should have a lot of this work in various stages of readiness and it would be a good time to jump on board for you (for testing purposes, it's not intended to be stable at this time though generally it's not a horrible experience. We try hard to keep the development branch fairly manageable to use).

You really don't have to know much to help out with development of new features, testing is a hugely important part of the puzzle.

---

### Post by CrazyGuy123 on 2008-05-20
I'm happy to do testing - debugging code I can do, just writing code from scratch means you'll be supporting it forever or until you can pursuade someone else to take over...

---

### Post by damoxc on 2008-05-20
I've tried the new modesetting in fedora 9 and I will say it's very nice.

---

