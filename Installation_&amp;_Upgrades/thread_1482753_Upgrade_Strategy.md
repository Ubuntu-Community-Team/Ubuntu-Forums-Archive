---
title: "Upgrade Strategy"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by solomonson on 2010-05-13
I am recovering from a failed upgrade and am formulating a solid upgrade strategy so I don't get burned again in the future.  Here are a few plans:
1.  Always have a data partition for stuff you want to save.
2.  Test the new version before the upgrade (not sure if it should be in a VM, off the LiveCD or what).
3.  Find a way to upgrade and keep the packages that I use.

#1 is very easy.  I plan on just having an ext3 partition that I mount for my home directory.

I would like to hear thoughts on #2.  I would really like to try out the new version with the packages I use most often.  I use several packages for development so downloading them all again gets quite time consuming.  Some are so cutting edge I even build from scratch.

For #3, I like the idea of a fresh install and running some script (or build) the packages that I used most often.  I'm also thinking maybe I could completely duplicate my OS partition and try the upgrade on it.  Then, if it works pave the old and if it fails pave the new one.  Then I always have an escape plan if things go south.

Any other hints?

---

