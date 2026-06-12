---
title: "virtual pc install question"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by TwoSeven on 2007-02-26
Hey folks,

Can someone tell me if the incorrect screen bitdepth issue has been fixed so that Ubuntu can be easily installed in Virtual PC.   

If it hasnt, has it been registered as a bug so that it will be fixed, if not could someone log it as I am unable to do so.

There is a manual work-around for this bug, but its a nightmare of ctrl-alt combinations and not at all condusive to new users or people who are new to the distro.

The bug:
Basically, when one tries to install 6.10 on a virtual PC, it messes up the screen because the xorg.conf file gets incorrectly set to 24 bits rather than 8 or 16 bits.   (The F4 screen settings get overridden and the Safe mode appears to use the xorg.conf file so is useless).

The fix could be a simple one - either in safe mode, get it to use an alternate xorg.conf file with a 16 bit or lower bit depth - or fix the installer so it correctly detects virtual PC, or fix the installer so the F4 display settings is actually used when the OS boots finally (and not discarded halfway thru).

Cheers.

---

### Post by Stewcort on 2007-03-17
I found my own answer her if it helps anyone else.

[http://arcanecode.wordpress.com/2007...-step-by-step/](http://arcanecode.wordpress.com/2007...-step-by-step/)

---

