---
title: "Tricky X problem"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by veritas366 on 2006-06-03
I have an older Gateway...actually several.  P3 processor at 600 mhz.  This one has a Radeon 7200 in it, though I've tried all of the steps below with an nvidia geforce 4 as well.  In fact, I even tried with an old 4mb pci vid card, just in case the AGP slot was the issue.

Here's the deal.  I've tried four distros on this machine.  Mepis 3.4.3, ubuntu Warty (just because I had that cd sent to me so I knew there'd be no burn issues), Gentoo and Damn small linux.  

Damn small linux is the only one that will boot live, though it didn't install (I left the room, so don't know if there was an error message).  However, it DID boot into x (uses fluxbox) and worked great as a live CD.

ubuntu live gets the boot progress bar all the way to the end...tries to start x (it appears) and then totally reboots.  Install goes into text mode and says "type gdm at prompt to boot into GUI" and then reboots if you do this.

Mepis simply gives me a blank screen when it tries to go to x. This also happens when booting in vesa mode.

Gentoo is the only distro that gave me an error message, though I don't think it tells me much more than that x is somehow the problem:

```
fatal IO Error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processes) with zero events remaining.
```

That's my only clue.  Now, as I said, DSL gets into fluxbox, so it may be something about kdm and gdm.  

So as I type, I'm downloading both Ubuntu and Xubuntu, but I"m wondering if anyone might have any ideas about what's going on. The monitor I'm on at the moment is a viewsonic a70f+ but that won't even be the monitor in use when this is done. 

Basically, the first distro I get to work is  the one I'll use.  Well, not DSL as this is for my mom and it needs to be a bit more user friendly, though DSL is cool.

---

