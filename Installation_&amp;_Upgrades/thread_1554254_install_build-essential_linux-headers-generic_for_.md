---
title: "install build-essential linux-headers-generic for kernel upgrade"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by bprins on 2010-08-16
Hi,

I'm trying to get kernel 2.6.35 up and running, but my wlan is not loaded in the new kernel.

in order to compile a manual downloaded wlan driver, i need to install 
build-essential, and linux-headers-generic for my kernel. But.. my wlan is not working. So there isn't much to sudo apt-get...

Now I'm pretty sure I'm not the only person who has this problem, so I bet there's an alternative way to install the build essentials for a specific kernel, from a different kernel. 

E.g, I boot kernel 2.6.32 (with WLAN) and there I install the build essentials for kernel 2.6.35. Is that possible somehow?

Many thanks in advance!

Bas

---

### Post by malikkabanis on 2010-10-03
same prob here
some body reply plz/..

---

### Post by bprins on 2010-10-04
I tried this under lucid, and I think I gave up in the end.

Maybe the wlan drivers aren't backported for that kernel version. I've installed maverick and there I don't have that problem.

Are you running lucid or maverick?

---

