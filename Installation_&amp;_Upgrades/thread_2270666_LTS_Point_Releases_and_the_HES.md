---
title: "LTS Point Releases and the HES"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by residualbit on 2015-03-24
My understanding is that main purpose of the LTS point releases, apart from just collecting all of the previous updates, is to use a newer kernel to allow for LTS support on newer hardware.

My question is, if I am running older hardware (~2010-2011) on a certain machine, is there any benefit to 14.0.2 vs. a fully-updated 14.04? There are some bugs/regressions with the latest point release, and I'm wondering if I not just better off on the initial release.

---

### Post by grahammechanical on 2015-03-24
The new Hardware Enablement stack is mainly meant for new installs. So, a new install of 14.04.2 will have the new Hardware Enablement stack. Existing installations will move on to Ubuntu 14.04.2 but not receive the new hardware Enablement stack without user authorisation. I am repeating what you already know for the benefit of those of us who do not know what we are talking about.

The point to keep in mind is that the kernels in 14.04 and 14.04.1 will be supported with security fixes until the end of 14.04 five year support period. But the kernels in 14.04.2 and later will not be supported as long. So, if we move on to 14.04.2 we must also move on to 14.04.3; 14.04.4 and finally on to 14.04.5 or upgrade to 16.04 when it comes out.

If every thing works well on this hardware, then what reason is there to upgrade the Hardware Enablement stack? On the other hand if the improvements made to Linux since April 2014 will fix some things that do not work as well as we like, then we have a reason to upgrade to the next Hardware Enablement stack.

A fully updated 14.04 will have all the updates that are in 14.04.2. The original 14.04 ISO image will not have those updates. So, that is why a new ISO image is created every six months or so.

Regards.

---

### Post by residualbit on 2015-03-24
So in general, if I am having issues with certain hardware specifically due to the HES and have no qualms about re-installing, I'm not losing anything by reinstalling 14.04 and just installing all of the updates?

Basically, I was running 12.04 happily on this machine, then went to 14.04, also happily, then experimented with it as a hackintosh. Now I'm back to Ubuntu, and not having a great time with 14.04.2.

---

