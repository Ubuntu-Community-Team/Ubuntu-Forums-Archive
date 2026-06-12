---
title: "Xserver crash anyone on recent updates ??"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2009-08-27
Well I have a XServer crash on recent updates (<3h) with **xserver-xorg-video-intel 2:2.8.1-1ubuntu1**

The crash says:
```

(II) Loading extension DRI2
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
dlopen: /usr/lib/xorg/modules/drivers/intel_drv.so: undefined symbol: resVgaShared
(EE) Failed to load /usr/lib/xorg/modules/drivers/intel_drv.so
(II) UnloadModule: "intel"
(EE) Failed to load module "intel" (loader failed, 7)
(EE) No drivers available.

Fatal server error:
no screens found

```

Anyone ??

---

### Post by vikrant82 on 2009-08-27
Frankly speaking I am not even able to get a failsafe X. The vesa and fbdev drivers seem to crash with following :

```

(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.4.0
	ABI class: X.Org Video Driver, version 5.0
(EE) module ABI major version (5) doesn't match the server's version (6)
(II) UnloadModule: "fbdev"
(II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(EE) Failed to load module "fbdev" (module requirement mismatch, 0)

```

---

### Post by vikrant82 on 2009-08-27
There seemed to be some some versions mismatch across various xserver PPAs. Now I am able to boot with vesa But still no luck with intel.

---

### Post by andresmh on 2009-08-27
My machine keeps crashing after a few minutes of using it. I suspect is just Xserver because I do ctrl+alt+backspace and it does restart X.

---

### Post by vikrant82 on 2009-08-27
Well it was a jumbled mess of various xserver ppas. Removed all ppas and reinstalled everything related to xserver to get a shiny desktop. :)

---

