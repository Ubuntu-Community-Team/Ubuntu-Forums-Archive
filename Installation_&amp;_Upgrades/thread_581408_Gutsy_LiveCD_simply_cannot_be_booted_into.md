---
title: "Gutsy LiveCD simply cannot be booted into"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Devz0r on 2007-10-19
Every LiveCD worked almost flawlessly (including Feisty) up to about Gutsy Tribe 5. The Beta and RC and official Gutsy wouldn't detect anything and I had to configure my screens and graphics manually.  Sometimes I got it to boot in Beta I believe, with visual distortion.  Now I cannot get it to boot at all in 7.10.  I get to the low graphics mode thing and no matter what I do (continue, configure), I still can't get past the boot script thing rc.something.  I press alt+f4 and it brings me to a terminal.  I type in startx and I get this:


(WW) RADEON: No matching Device section for instance (BusID PCI:2:0:1) found.
(EE) No devices detected.

Fatal server error:

no screens found

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.


I am guessing it isn't working with my monitor or video card, but why does it work in other releases?  I'm sorry, I love ubuntu and recommend(ed) it to everyone, but this is the most disappointing release.

Widescreen AOC 22LVWk LCD monitor with DVI
Radeon x1850

---

### Post by ajgreeny on 2007-10-19
Have you checked your CD download and burn?

---

### Post by Pumalite on 2007-10-19
Follow #2's advice; also install with Alternate CD. You might have to configure the xserver at the end of the install anyway.

---

