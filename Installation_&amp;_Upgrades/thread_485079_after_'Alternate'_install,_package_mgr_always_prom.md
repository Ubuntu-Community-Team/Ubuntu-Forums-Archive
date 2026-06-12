---
title: "after 'Alternate' install, package mgr always prompts for original CD?"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2007-06-26
I did a fresh install of Ubuntu 7.04 using the 'Alternate' CD and setting-up a sw RAID-1 (mirror) on two SATA drives.  Everything installed fine and my desktop is now running (and updating) normally.  But anytime I install a new app through Add/Remove programs, it prompts for the original install CD?  It never did this when I installed with the 'regular' CD.

Does anyone know what is different, or how I can fix this?

---

### Post by dabl on 2007-06-26
Yep, it's fixable.  I'm away from my rig, so I'll try to remember.  Your Alternate CD is set up as a "source" in Synaptic, so you need to open Synaptic, and I think there is a tab on the top edge called "Sources", and you can go in there and un-check a box, or maybe highlight the CD ROM source and then choose "remove" at the bottom of that screen.  I hope this is approximately correct  [-o<


P.S. -- where did you find guidance on setting up that RAID array?  Thanks!

---

### Post by bsmith1051 on 2007-06-26
> **dabl said:**
> Your Alternate CD is set up as a "source" in Synaptic, so you need to open Synaptic, and I think there is a tab on the top edge called "Sources", and you can go in there and un-check a box

P.S. -- where did you find guidance on setting up that RAID array?  Thanks!
You were right,  the CD was selected as a source!

re software mirror, here's my earlier post (with solution),
[http://ubuntuforums.org/showthread.php?t=481499](http://ubuntuforums.org/showthread.php?t=481499)

---

### Post by dabl on 2007-06-26
> **bsmith1051 said:**
> 
re software mirror, here's my earlier post (with solution),
[http://ubuntuforums.org/showthread.php?t=481499](http://ubuntuforums.org/showthread.php?t=481499)

Cool -- thanks!

---

