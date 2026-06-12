---
title: "Upgrading Kernel undoes all previous modifications"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by azmanam on 2008-07-18
**
Gateway box
P4 3GHz processor
1 GB RAM
one 40 GB Western Digital IDE Hard drive
one 500 GB Western Digital IDE Hard drive
NVidia-GeForce FX 5200 DDR 128MB Video Card
Hauppauge HVR-1600 Tuner Card (with accompanying remote of unknown model #)
Creative Sound Blaster X-Fi Card
kernel 2.6.24-19-generic
**

I suppose it makes sense that upgrading the kernel would overwrite all files with the new, upgraded ones.  

However, I have some outstanding issues that have been corrected by appending or otherwise customizing a few files such as /etc/modules, /boot/grub/menu.lst.  

When I upgrade the kernel, the customizations are erased and replaced with the file that I suppose is downloaded during upgrade.

Some of the customizations are rather time consuming to download and install all files, etc.

My question is: can I write something that I guess would be the equivalent of a batch file or a macro that I can run once and will download necessary files, append necessary files, etc?

Thanks!

---

