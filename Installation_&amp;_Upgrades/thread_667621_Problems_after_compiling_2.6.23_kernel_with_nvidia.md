---
title: "Problems after compiling 2.6.23 kernel with nvidia"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Jungleboss on 2008-01-14
I have compiled kernel 2.6.23.12 AMD64 according to the master kernel guide. I then install the NVIDIA driver again (from nvidia.com, same version as for the old kernel). When gdm starts i only get into a low graphics mode, with the text "Your screen and graphics card could not be detected correctly).
I have tried my old xconf.org file (working in the old kernel (2.6.22.14) and tried to let Nvidia generate a new with nvidia-xconfig. None of them works. I can boot my old kernel without problem.

My kernel is compiled as a x86_64 generic (I've also tried the more specific core2 compilation parameter). I have both tried Nvidia driver 100.14.19 and 169.07 (newest).
Can it be some problem with Nvidia kernel modules?

My nvidia-installer.log shows no errors.

---

### Post by Partyboi2 on 2008-01-15
You could give envy ago
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Jungleboss on 2008-01-15
Thank you very much!! With Envy it now works!

Btw the new kernel really feels faster.

---

