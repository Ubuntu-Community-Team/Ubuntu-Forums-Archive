---
title: "How long does it take.  Frozen?"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Mookie1171 on 2009-12-30
Hi.  I'm installing ubuntu for the first time on a comp.  It is first formatting the hard drive and then installing the ubuntu.  But it may be stuck.  Its been on this one step for a few hours and the progress bar hasn't moved.  It is the partitions formatting step.  Creating ext4 file system for / in partition #1 of SCIS (0,0,0) (sda)...   Its been stuck at 5% for the last few hours and the mouse cursor won't move when I move the mouse.  Does this mean its frozen and I need to restart it and try to install again or is it supposed to take this long?  Actually I already restarted and tried again once and now its back at the same spot. I can't tell if its frozen or not.  help.

---

### Post by audiomick on 2009-12-30
> **Mookie1171 said:**
> Hi.  I'm installing ubuntu for the first time on a comp.  It is first formatting the hard drive and then installing the ubuntu.  But it may be stuck.  Its been on this one step for a few hours and the progress bar hasn't moved.  It is the partitions formatting step.  Creating ext4 file system for / in partition #1 of SCIS (0,0,0) (sda)...   Its been stuck at 5% for the last few hours and the mouse cursor won't move when I move the mouse.  Does this mean its frozen and I need to restart it and try to install again or is it supposed to take this long?  Actually I already restarted and tried again once and now its back at the same spot. I can't tell if its frozen or not.  help.

It sounds like it is stuck. A couple of hours is too long.

I don't know if it is the best advice, but I would boot into the live CD and try the partitioning tool from there and see if it still has a problem.
(from the Live CD system> administration> gparted
If that still doesn't work, I'd be starting to wonder if the HDD is really healthy.

---

### Post by Mookie1171 on 2009-12-30
I'm booting from a boot CD.  It gives me the option to Install them side by side, choosing between them each startup, erase and use the entire disk, or specify partitions manually.  whatever I pick it freezes when it starts partitioning

---

### Post by Bartender on 2009-12-30
How much RAM you got?  I've tried installing to PC's with minimal RAM (300 or thereabouts) and it took FOREVER.  Added some RAM and it went a lot faster.

---

