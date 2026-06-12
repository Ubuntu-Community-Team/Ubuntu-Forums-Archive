---
title: "Problem was fixed then it returned (errno=-16)"
date: 2008-10-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SpinningAround on 2008-10-30
I downloaded Ubuntu RC 8.10 today, when using LIVE CD did this message pop-up a few times before it continued as normal.
> 
Buffer I/O error on device sr0, logical block (6 random nr)

Then after the installation was finished did I reboot and removed the CD, then while ubuntu was booting up did the boot halt with this error message
> 
ata3 COMRESET failed (errno=-16)
reset failed giving up


The interesting part is that I did use Ubuntu beta that I downloaded a shot while after beta was made available and there did I not have this problem. The first error message from the live CD did turn up but after that did the system work fine.

I found a bug report on it [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/256637)

---

