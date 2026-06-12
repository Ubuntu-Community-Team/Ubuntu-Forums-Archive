---
title: "No nvidia graphics on 3.5.0-rc3 kernel"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by N00b-un-2 on 2012-06-19
I just built the latest kernel from source and all went well, except when I boot into the new kernel I  have no graphics acceleration.  When I boot into the other kernel (3.2.something) I have nvidia drivers.  I'm guessing it has something to do with DKMS not building modules for the newest kernel.

is there any way to force DKMS to build the modules, or is there a way to compile the kernel with the proprietary drivers as a module?

I'm going to take a crack at install the nvidia drivers from source directly from nVidia (the old method where you drop out to the tty) and see what happens

---

### Post by N00b-un-2 on 2012-06-27
xorg edgers PPA fixes the issue

---

### Post by bogan on 2012-06-27
Hi!, [B]NOOb-un-2,
[/B]
You Posted:>  xorg edgers PPA fixes the issue 	 Glad to hear that you got it fixed!
Please would you Post some details of what you actually did?

What video card do you have? and,  Did you just install the nvidia-current from xorg edgers PPA, with 'apt-get'?

If so, what version was installed?

Chao!, **bogan.**

---

### Post by N00b-un-2 on 2012-06-28
It's an EVGA Geforce 8400 GS 1GB DDR3.  it's device ID is 10c30x10de.  And yes, just apt-get install nvidia-current fixed the problem.  The issue was indeed with DKMS not working with the new kernel for certain proprietary drivers, but the xorg-edgers packages fix the issue.

---

