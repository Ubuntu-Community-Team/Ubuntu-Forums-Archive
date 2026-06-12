---
title: "Freezes at Booting the kernel"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by soyamilk on 2007-09-26
Hi guys,
Can't install Ubuntu on my laptop.(A9Rp NB Celeron M 420 1.6GHz/15"/512MB/80GB/DVD+-RW) It freezes after "Booting the kernel..." The cd is ok for sure,  installed Ubuntu from it on my desktop. 

Found some threads with the same problem, tried everything suggested but nothing worked. Can anybody give the certain answer?  Is it a kind of bug, or should I try something else to do my with my machine? 

10x.

---

### Post by dabl on 2007-09-26
You say "freeze", but maybe not ...

When it is "frozen" for a few minutes, try Alt-F1.  If nothing, try Ctrl-Alt-F1.  If either of those gives you a login prompt, then it is only a video driver problem.  You can follow this guide to set up a VESA GUI, and then proceed to find the correct driver for your graphics chip:

[http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

:)

---

### Post by soyamilk on 2007-10-04
Already made it install. acpi=off helped.

---

