---
title: "NVIDIA GeForce 4 MX NV18 on 12.04"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by christophewk3 on 2012-06-18
Hi,

I have been trying to set up an old machine which has a NVIDIA GeForce 4 MX NV18 graphics card. Unfortunately I didn't find any working graphics driver. Using the open source nouveau driver resulted in heavy flickering, general distortion, and a black bar on top of the screen. Then I tried two versions of the Nvidia's binary driver, but the older one doesn't support KMS and the newer one doesn't support the graphics card. The screen resolution using the vesa driver is even worse. I did try installing the updated packages from the xorg-edgers fresh X crack ppa, but this didn't change anything. Am I missing anything?

Christophe

---

### Post by bogan on 2012-06-18
Hi!, **Christophewk3,**

According to the nvidia >driver web page the Legacy driver 'x86' would be the 'correct' driver but it is not compatible with the current Xserver, and the GeForce 4 MX series is no longer supported for Linux.

Sorry I cannot be more helpful or hopeful.

Chao!,** bogan**.

---

### Post by christophewk3 on 2012-06-26
Hey,

I have been able to solve some of the problems by switching to the most recent X.org packages and the 3.5 kernel from xorg-edgers[1], and disabling TV out (options nouveau tv_disable=1).

Maximum screen resolution is 1024x768 and Linux 3.5 breaks my DVB-T driver.[2] :-(


[1] [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
[2] [https://github.com/tmair/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/](https://github.com/tmair/DVB-Realtek-RTL2832U-2.2.2-10tuner-mod_kernel-3.0.0/)

---

