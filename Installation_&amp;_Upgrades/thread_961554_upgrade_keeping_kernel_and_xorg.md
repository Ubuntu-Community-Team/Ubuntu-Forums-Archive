---
title: "upgrade keeping kernel and xorg"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Elric27 on 2008-10-28
Hello. My following problem (and doubt) is that the intrepid's kernel cannot manage ndiswrapper and ati driver sucks with new xorg.
Therefore, I thought of holding back the kernels, and xorg package, as well as its dependencies, and later on, adding intrepid's repos and downloading the ubuntu-desktop metapackage from intrepid, meaning that all but xorg and kernel will be downloaded. I might have problems since xorg is included in the ubuntu-desktop but I think I can manage through aptitude.
My question is, is this safe encough? You think it will work? I need ndiswrapper for my Broadcom4312 (b43 and wl give me a poor signal, tried it all). If I upgrade -d, will xorg be kept if held?
Thanks a lot, sorry for another post on upgrade but didn't find any on this particular subject.

---

### Post by lemming465 on 2008-10-30
The library dependencies are complicated enough that I'd strongly suggest **not** upgrading if you hate the wifi and video drivers.  I sympathize; I have a multi-boot Toshiba laptop which has Atheros and ATI driver issues under 8.10.  In your shoes, I'd squat on 8.04 for another six months and see if 9.04 was better.

---

