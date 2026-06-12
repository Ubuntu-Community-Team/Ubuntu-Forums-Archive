---
title: "Restricted driver help needed for NVidia"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by tedbellinger on 2007-12-29
My restricted driver works under the -386 kernel but not under the generic kernel.

I was running Linux kernel 2.6.22-14-386 on the following hardware:
Dell Precision 420 MT (with dual 866 MHz P-III)
256 MB RDRAM
RIVA TNT2-based Diamond Viper V770D AGP video card

I loaded the generic kernel from the boot menu to get SMP support, but the NVidia driver won't run under this kernel. If I go back to the -386 kernel, everything works fine again.

I would like to enable SMP support to take advantage of both processors, and enable a video driver that will allow resolutions higher than 800x600.

1. The NVidia site has a display driver for these cards under Linux Display Driver - x86, Version: 71.86.01: NVIDIA-Linux-x86-71.86.01-pkg1.run.
(see [http://www.nvidia.com/object/linux_display_x86_71.86.01.html](http://www.nvidia.com/object/linux_display_x86_71.86.01.html)) Should I try this? If I do not install the driver using the restricted drivers manager, are there any risks I should know about. Is there a way to get to it through the restricted drivers manager?

2. Would this be any easier if I got the -686 kernel? If so, how do I get it if it does not show up in Synaptic?

---

### Post by Pumalite on 2007-12-29
It's better to run a generic kernel in my opinion. Number one looks good to me.

---

### Post by tedbellinger on 2007-12-29
Why is generic better than -686?  I thought -686 was for P-II and newer.

---

### Post by Pumalite on 2007-12-29
Actually '386' is better for older computers. Newer ones: generic. This is mine:
pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
pumalite@pumalite-desktop:~$ 
(i686 is right, as well as generic)

---

### Post by oldsoundguy on 2007-12-29
The driver is determined by the CARD and not the processor on the motherboard.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  is a software program to get the appropriate nVidia driver.  However, I have not used it and just installed the generic.  Works fine, but I am not a gamer and do not need whizz bang golly gee whizz 3D rendering and graphics. This program (Edgy) comes with glowing reports of success but YMMV!

---

