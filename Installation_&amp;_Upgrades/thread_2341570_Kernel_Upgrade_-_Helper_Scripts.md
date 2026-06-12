---
title: "Kernel Upgrade - Helper Scripts"
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by mets_web on 2016-10-29
Hi All -

Often users need a way to update the kernel a bit sooner than the packages are available through standard channels (apt, aptitude, etc.).
Not talking distribution version upgrades (e.g. 14.04 -> 16.04) but talking the kernel (e.g. 4.8.4 -> 4.8.5).

If that's you and you'd like an "easy" way to get it done, here's some help:

[https://github.com/mtompkins/linux-kernel-utilities](https://github.com/mtompkins/linux-kernel-utilities)

There's also a video to give you some background here:

[https://youtu.be/CokrHUykkUQ](https://youtu.be/CokrHUykkUQ)

There's no magic here, just some bash scripts to help you through the process. The compiled kernel is pulled from Canonical.
 Everything can be inspected within the scripts before executing.

If you are a bit more advanced, there are also scripts to compile a kernel.

---

