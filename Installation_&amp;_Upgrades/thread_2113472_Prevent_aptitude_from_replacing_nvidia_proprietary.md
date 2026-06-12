---
title: "Prevent aptitude from replacing nvidia proprietary drivers"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by ivles on 2013-02-07
Hi,

I have a bit annoying problem. I have a GTX 570 and I use proprietary drivers because I develop on CUDA and Compute Shaders (OGL 4.3). The problem is that when I do an upgrade, aptitude overwrites the link to libGL.so provided by nvidia. Thus, I have to manually reinstall proprietary drivers each time I do an upgrade.

For now, the solution I found is to put the concerned packages on hold but now I'm stuck because I can't upgrade anymore (lastest KDE upgrade dependencies)

Is there any way to be able to upgrade without overwriting the proprietary drivers ?

---

