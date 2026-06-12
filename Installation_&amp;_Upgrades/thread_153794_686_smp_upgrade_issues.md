---
title: "686 smp upgrade issues"
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by mrose2n on 2006-04-01
I'm new to the Ubuntu scene.  I installed the x86 image and was running the 386 kernel.  My processor is an Intel dual core, so I tried upgrading to the 686-smp kernel.  When I boot into the 686, it works fine for about a minute, then the mouse gets all "jumpy" and I can't click on anything.  If I open the system monitor within the first minute, I notice that CPU1 stays @ zero and CPU 2 jumps from zero to 100%, back and forth.  If I load back into 386, the screen resolution is stuck @ 640 x 480 and I can't change it.  Next I tried 686 (not smp), which seems to work fine, but I want to take advantage of my dual-core architecture, any ideas?

UPDATE:  I reconfigured my graphics drivers and, so far, the problem seems to have gone away.  The solution that worked for me was the one given in this thread, if anyone is interested:  [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

