---
title: "virtualized linux, on windows, with 3D acceleration?"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by skullmunky on 2008-10-06
I have a 3D app (to be precise, a game built around quake 3 arena).  I made it for linux, but now need to run it in one special case in Windows.  I want to see if running VMWare or another virtualization server would work - but, because it's quake 3, it needs to have some level of decent 3D driver acceleration.  So there's my question - will virtualized linux with nvidia drivers work?


(I don't have Windows and don't want to buy VC++ or suffer through the agony of building a cross-compiling toolchain for this monster unless absolutely necessary. )

---

### Post by cariboo on 2008-10-06
It depends on your virtualization software. You have to know if it actually accesses the hardware, or as in the case of vmware and virtualbox where they create virtual hardware. I had the same problem running Microsoft Bob on top of Windows 98, I couldn't get any better resolution than 640X480.

Jim

---

