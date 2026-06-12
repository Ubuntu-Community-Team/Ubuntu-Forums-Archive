---
title: "Running a patch every time a kernel upgrades"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2011-07-13
This morning I ran the automatic upgrade provided on the repositories, updating my kernel from 2.6.38-8 to 2.6.38-10.

Unfortunately, upon reboot I discovered that a series of patches I'd applied in order to get my wireless card on my desktop working had been undone (see [http://www.thetechgame.com/Forums/p=10218362.html](http://www.thetechgame.com/Forums/p=10218362.html)). I had to run a modified version of the instruction set in order to get my wireless back on.

My question: is there a way to trigger this every time the kernel upgrades? I'd hate to have to run this cumbersome set of commands manually every time.

FYI I'm running Ubuntu 11.04, i686 arch.

---

### Post by dino99 on 2011-07-13
better to file a bug to get a fixed kernel:

ubuntu-bug linux

---

### Post by patman0623 on 2011-07-13
Done.

---

