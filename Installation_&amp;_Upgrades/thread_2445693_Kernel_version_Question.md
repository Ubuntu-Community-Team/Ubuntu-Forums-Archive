---
title: "Kernel version Question?"
date: 2020-06-18
forum: Installation &amp; Upgrades
---

### Post by spiderbait on 2020-06-18
Hi every ones,new to Linux and was wondering as my Ubuntu 20.04LTS came with version 5.4.0.33 is it ok to merge to the latest 5.7 without following the 5.4 family?
Any advantages?
And if so,why continuing to develop the 5.4 if the newest 5.7 or 5.8 is better??

---

### Post by CatKiller on 2020-06-18
> **spiderbait said:**
> And if so,why continuing to develop the 5.4 if the newest 5.7 or 5.8 is better??

Ubuntu is not a rolling release distro. The versions of software are fixed at the time of release (with some limited exceptions), but security and bug fixes are backported to those versions. Kernel updates come to the Long Term Support releases from the later short term releases through the Hardware Enablement stack. 

Participating in kernel testing isn't really something to recommend to someone that's new to Linux but, if you want to, it's your machine.

---

### Post by ActionParsnip on 2020-06-18
If you are asking then I don't suggest you start messing with kernels without a lot of research. One way to know is; is all of your hardware working? If yes then you don't need to change kernels.

---

### Post by grahammechanical on 2020-06-18
This forum has a Ubuntu development version section where those experimenting with the very latest kernels exchange comments. Those brave people have already moved on to 5.8

[https://ubuntuforums.org/showthread.php?t=2445465](https://ubuntuforums.org/showthread.php?t=2445465)

This is their 5.7 thread

[https://ubuntuforums.org/showthread.php?t=2440607](https://ubuntuforums.org/showthread.php?t=2440607)

One thing I learned from running a release candidate kernel is that proprietary video drivers may not work as they have not been patched for the kernel. I gave up experimenting with release candidate kernels because my video card was so old and the video driver (proprietary or open source) was not patched for the kernel.

I do run the Ubuntu development version so I do get these kernels eventually and the OS does not fall over. So, if you want to experiment then dual boot Ubuntu LTS with another install of Ubuntu that you will not mind re-installing.

Regards.

---

