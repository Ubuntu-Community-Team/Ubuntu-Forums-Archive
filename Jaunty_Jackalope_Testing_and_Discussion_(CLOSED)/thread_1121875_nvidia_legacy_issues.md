---
title: "nvidia legacy issues"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ranmanh on 2009-04-10
Hi,

after upgrading to the 9.04 beta my old nvidia card (geforce) stopped working, or better to say the X refuse to start because, even finding the "nvidia" module it cannot loaded due to:

I) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
 dlopen: /usr/lib/xorg/modules/drivers//nvidia_drv.so: undefined symbol: Allo cateScreenPrivateIndex
 (EE) Failed to load /usr/lib/xorg/modules/drivers//nvidia_drv.so
 (II) UnloadModule: "nvidia"
 (EE) Failed to load module "nvidia"

It does not matter if installing the the drivers through envyng (version 08), compiling the latest from Nvidia (version 09), it always crashes.

Only works installed the precompiled: xorg-video-nv drivers, which are called as "nv" in the /etc/X11/xorg/conf, and it screws up the screen resolutions.

Any idea/workaround, anybody did anything at all in these respects?

I have tried for the last 3 days without finding any suitable solution

Thanks very much

Ran

---

