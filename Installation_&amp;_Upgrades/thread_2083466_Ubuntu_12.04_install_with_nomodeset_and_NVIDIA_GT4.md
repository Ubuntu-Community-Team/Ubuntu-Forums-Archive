---
title: "Ubuntu 12.04 install with nomodeset and NVIDIA GT420"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by kracheck on 2012-11-12
While installing the new Ubuntu 12.04 LTS 32bit Desktop Edition I ran into some problems that can be attributed to the graphic card (in my case a NVIDIA GT420) making the installation impossible (blank screen). Should you experience similar problems with other cards you might consider the following approach.

Installation of 32bit Desktop Version

*Download the current iso and burn it on a CD.
*When booting off the livecd press the space bar when you see the tiny 'human' logo down the bottom.
*When you get the alternate menu select boot options (F6) and select nomodeset.
*Continue with the LiveCD boot.

Once installed go into the GRUB menu and select the OS that needs to boot and type 'e' (as in edit)

Look for the line containing "quiet splash". After that and before the next thing to it, enter "nomodeset" (without the marks).

When you are in the OS Ubuntu will detect the card and let you install the NVIDIA's proprietary graphic card driver

---

### Post by ercherramon on 2012-11-12
hi. good recommendation. i try too. and add always:

```
 --xforcevesa nomodeset b43.blacklist=yes noapci irqpoll 
```

and it works for me in the installation process.

---

