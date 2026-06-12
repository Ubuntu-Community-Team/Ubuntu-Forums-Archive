---
title: "nVidia problem on 64bit computer"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by mosestruong on 2008-06-16
After upgrading the kernel to 2.6.24.18-generic, my nVidia driver no longer works, I get the dialog asking me to specify another driver. 

I have a GeForce Go 7200 video card on my HP pavilion computer.

uname -a:
Linux ebenezer 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

I've checked and I have the following packages installed:

linux-image
linux-image-2.6.24.18-generic
linux-image-generic

linux-restricted-modules-common
linux-restricted-modules-generic
linux-restricted-modules-2.6.24.18-generic
linux-restricted-modules

linux-ubuntu-modules-2.6.24.18-generic

nvidia-glx-new
nvidia-kernel-common

I've tried raising a bug [https://bugs.launchpad.net/bugs/239897](https://bugs.launchpad.net/bugs/239897)
but was asked to submit more information - does anyone know what other information I can submit? Or better still, know of a solution to this problem? thanks.

---

### Post by oldos2er on 2008-06-16
Are you able to log in to a graphical desktop? If so, go to [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and download and run EnvyNG. Hopefully that will fix your video problems.

---

### Post by mosestruong on 2008-06-23
I've tried installing EnvyNG, but that didn't work.

However, if I install nvidia-glx instead, it works, but is very unstable... it causes Firefox 3 to continue to be unresponsive, and also caused X to crash more than 3 times in just a few hours...

---

