---
title: "building own kernel results in no sound devices"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by eldragon on 2008-08-28
ive decided i needed to know how to build kernels. dont ask why, i know it will be useful in the near future, and i decided to use the kernel.org kernels in order to be more ubuntu-independant. again, i dont know why. its just that i needed to break the laptop somehow. 

followed this guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

and after serveral attempts, i built and configured successfully kernel 2.6.27-rc4-git7

i learned quite a bit in the process. yet not enough.

i copied my old config file for the running default kernel from /boot to /usr/src/linux (symlinking the new kernel to build to /usr/src/linux).
then ran menuconfig and did some experimental tweaking (especially with power management options, that are experimental, and disabled by default...probably not present in my old .config file).


twice i built the kernel, with different settings, and both times i end up with no sound.

am i missing something? are there any restricted modules not included in the git kernel?

im quite a noob concerning kernel building, so bare with me :D

thanks

---

