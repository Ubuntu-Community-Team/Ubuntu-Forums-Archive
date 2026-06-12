---
title: "X server fails to start; drm error"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by sveta on 2009-12-21
Hi,

I am running ubuntu 9.10 on Sony vaio z11. I followed the instructions to install poulsbo driver for 3d support at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

It did not work for me and I could only boot with save mode and only when i915 is in the blacklist.

To revert the changes I uninstalled all psb packages  modules except psb-kernel-headers which gives an error "subprocess installed post-removal script returned error exit status 1" when I try to uninstall it. 


I changed the xorg-conf back to original (no NVIDIA). 
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


Section "Device"
    Identifier    "Configured Video Device"
EndSection

```

When  i915 in the blacklist.conf X can start in safe mode only.
DRM log is:
```
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```



When i915 is NOT in the blacklist X does not start



Xorg.conf output:

```
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 2.9.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]



```


I get an error in DRM log:
```
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
**/usr/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers//intel_drv.so: undefined symbol: drmCheckModesettingSupported**
```




Do you have any suggestions on how to fix the problem and go back to the original 9.10 configuration (without 3d support)?

thank you in advance,
Sveta

---

