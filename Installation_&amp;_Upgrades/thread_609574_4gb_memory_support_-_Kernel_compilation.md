---
title: "4gb memory support - Kernel compilation"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by Deksan on 2007-11-11
Hi,
Iwas using ubuntu 7.10 and have recently upgraded my computer with 4gb of memory.
I was using linux kernel 2.6.22-14-generic but only 2gb of memory was visible. After recompiling the kernel into a 2.6.22-9-custom and after adding PAE support, ubuntu can see the 4Gb of memory. The pbm is that now I dont have anymore audio device :( 
It seems i was using the kernel module :

/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko

though I dont have the "ubuntu" folder after compiling the kernel. I was wondering if anyone knew how to get the source of that /ubuntu/* in order to compile it ?

Thanks for ur help

---

### Post by Deksan on 2007-11-13
Found out that the module for my sound card wasnt activated after the copy .config of the  ubuntu kernel and after manually enabling it in make menuconfig  solved the pbm. Still dont know why i have to do that thought the .config will carry the same modules. Maybe there was a more elegant way to do it ...

---

