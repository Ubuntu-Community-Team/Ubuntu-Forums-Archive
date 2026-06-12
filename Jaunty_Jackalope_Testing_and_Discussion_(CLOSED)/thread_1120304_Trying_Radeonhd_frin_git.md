---
title: "Trying Radeonhd frin git"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by super.rad on 2009-04-08
I'm about to try out the Radeonhd driver from git (following [this guide]("https://help.ubuntu.com/community/RadeonHD") )
In the "Getting DRM Kernel Modules" section it says
> These commands also assume you're running the kernel provided by UbuntuI'm using the 2.6.29.1 kernel from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"), will this still work the same or should I go back to the regular .28 jaunty kernel to try this?

EDIT: Went for it anyway as if it didn't work I'd just drop back to the .28 kernel, all seems to be working. Performance is pretty good but the last steps are:
```
cat /var/log/Xorg.0.log | grep "Direct rendering enabled"
```
which should say:
> (II) RADEONHD(0): Direct rendering enabled

but mine is saying:
> (WW) RADEONHD(0): Direct rendering for R600 an up forced on - This is NOT officially supported at the hardware level and may cause instability or lockups

Also just noticed the typo in the title, could a mod please change it to "Trying Radeonhd **from** git"

---

### Post by rbmorse on 2009-04-08
THe warning is correct. The drm and kernel modules radeonhd requires for DRI on RV6XX chipsets are still considered "experimental."  

I think I saw somebody mention that the very latest update to the xorg packages in Jaunty's repository now support DRI for both Radeon and RadeonHD on RV6XX, so it may not be necessary to build the mesa modules from that git any longer. 

I also saw some discussion today on the radeonhd IRC channel about packaging what they have now as a new release but I had to leave before they came to resolution. At any rate, it seems to be close. Will not include full hardware accelerated 3D for RV6/RV7, but should support Xv video playback.

---

### Post by super.rad on 2009-04-09
Thanks, I tried the Xorg and RadeonHD from jaunty's repo's and they work exactly the same for the DRI. I'll just stick with those for the time being

---

### Post by super.rad on 2009-04-09
Radeonhd 1.2.5 was released today, is there any chance of seeing it in Jaunty or is it too late by now?
[http://lists.freedesktop.org/archives/xorg/2009-April/044968.html](http://lists.freedesktop.org/archives/xorg/2009-April/044968.html)

---

