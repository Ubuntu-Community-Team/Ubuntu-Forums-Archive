---
title: "System monitor"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by Ziggurat on 2008-03-06
Hi, i installed Ubuntu hardy 2 days ago and everything was working ok. Today ive made an update and i think a new kernel was installed.

Before the update the system monitor showed the 4 CPUs of my quad proccesor and now shows only one.

Anyone knows anything about this?

Thanks!

---

### Post by prshah on 2008-03-06
post the output of `uname -m` for a clue. If you have installed a stock i386 kernel instead of a i686 kernel, you might lose SMP (multi processor) capability.

Cheers,
PRShah

---

