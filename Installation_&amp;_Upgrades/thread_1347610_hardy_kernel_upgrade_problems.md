---
title: "hardy kernel upgrade problems"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by macho on 2009-12-06
There was a recent hardy upgrade that included some kernel stuff that I think is causing me some problems.  I rebooted to find my wireless no longer working.

$ sudo modprobe rtl8180
FATAL: Module rtl8180 not found.

So I'm now missing my networking module.  I *think* it's supposed to be in linux-backports-modules-2.6.24-25-generic, which I have installed, however:

$ uname -r
2.6.24-26-generic

is the 25 vs 26 the problem, i.e. do i have to install linux-backports-modules-2.6.24-26-generic to solve the problem?  i would just try it, but packages.ubuntu.com seems to be down right now, plus, if this is the problem, i'd like to know where to report this upgrade bug, since it could really leave folks in the cold, but i don't know where i should do that.

if this isn't the problem, maybe folks could give me some other ideas of what it might be.

thanks.

---

