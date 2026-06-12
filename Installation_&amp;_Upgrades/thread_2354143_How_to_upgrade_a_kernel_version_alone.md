---
title: "How to upgrade a kernel version alone?"
date: 2017-02-28
forum: Installation &amp; Upgrades
---

### Post by pradeep8985 on 2017-02-28
Hi,

I am new to ubuntu. I am currently using ubuntu 14.04.3 with kernel version 3.19.0-25.  I have to upgrade the kernel alone. Please let me know how can i do this?


Regards
Pradeep

---

### Post by ian-weisser on 2017-02-28
Moving away from the system-provided kernel is possible, but introduces an administrative burden and other headaches. If you are truly new to Ubuntu, you may not yet understand the full implications of your question.

If you have a problem with your system, it would be better to tell us about the problem.

---

### Post by ubfan1 on 2017-02-28
With 14.04.3, you are already running a Hardware Enablment Stack with a later kernel.  The 14.04.5 release has a later HES, with a later kernel.  Take a look at the installed packages with "lts" in their name -- the newer ones have a later name for the release.  Usually, the HES comes with X server upgrades as well as kernels, but I recall I did have success (on a 14.04 system) just installing a 4.4 kernel and its firmware package.

---

