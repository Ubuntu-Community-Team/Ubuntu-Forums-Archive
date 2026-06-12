---
title: "Downgrading 10.10 to 10.04 kernel"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by hoover67 on 2011-01-11
Hi folks,

due to stability issues discussed elsewhere¹, I've decided to give the 10.04 lucid LTS kernel a try on my freezing / crashing mint10 system (based on Maverick). I downloaded the kernel-image-generic deb file from the lucid update repos and it installs and boots just fine. 

However, when I try to start tvtime (my favourite tv program), I get the following error message: 

```
** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

```

I've tried googling, but most stuff seems related to ati cards (I have an nvidia 6200 which works just fine with tvtime on the stock mint 10 / maverick kernel, 2.6.35.xxx). 

I was wondering what I'm missing in the 2.6.32 kernel setup that might prevent tvtime from working correctly with that kernel. I'm using the nouveau driver for that matter, last night I tried running the nvidia prop. drivers (173, 96) but then Xorg didn't start anymore until I removed the proprietary drivers. 

Thanks in advance for any ideas, 

Uwe
1: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

---

