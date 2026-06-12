---
title: "686-SMP kernel first, or the 187 updates first?"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2006-10-31
I just installed Ubuntu 6.0.6 LTS (Dapper) on a PC with HyperThreading P4 processor, which really calls for the linux-686-smp kernel, not the 383 default one.

The interesting thing is... before I even got a chance to upgrade to the 686-smp kernel, I was prompted for 187 updates (~209MB)!

Since I want my Ubuntu workstation to run optimal code as much as possible and so it occurred to me that:

1. If I install the linux-686-smp kernel first, will all the 187 updates be 686 optimized too?

If so, what would happen if I mistakenly installed the 187 updates first (386 of course, because the kernel is still 386) and only then upgrade to linux-686-smp kernel? Will I be prompted for re-updating those 187 updates?
 If not, does this mean that my applications run sub-optimally?

Thanks!
Alex

---

### Post by x64Jimbo on 2006-10-31
Run your kernel upgrade first - make sure everything is cool. Then install the updates as necessary.

---

### Post by x64Jimbo on 2006-10-31
Run your kernel upgrade first - make sure everything is cool. Then install the updates as necessary.

---

### Post by xp_newbie on 2006-11-01
Oops... I mistakenly installed the 187 updates before upgrading the the kernel. :(

Does that mean that I am now running an non-optimized versions of the various libraries and applications?

What is the best approach to fully utilize my CPU's power using Ubuntu?

Thanks!
Alex

---

