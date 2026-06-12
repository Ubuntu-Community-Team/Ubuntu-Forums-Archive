---
title: "YANPP (Yet another nVidia problem post)"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by elventear on 2007-05-08
Hi,

I recently updated to Feisty and I am having some problems with with the nVidia driver for X. Basically, I don't know what the heck is going on, which driver to install and all that. 

My video card is an nVidia GeForce MX 420 I have tried with nvidia-glx, nvidia-glx-new and nvidia-glx-legacy and it doesn't really work. I when do dmesg I get the following:

The NVIDIA GeForce4 MX 420 installed in this system is supported through the NVIDIA 1.0-96xx Legacy drivers. 

This is with the nvidia-glx-legcy installed, using the nvidia-glx hasn't been a success either. So I am assuming there is some file laying around that is compiled against the nvidia-glx-new. I've tried removing everything nvidia-* and it hasn't been much help either.

I would appreciate any ideas on how to search for the problem and fix it.

On a side note, following some suggestions available on the forums, I get the linux-restricted-modules-2.6.20-15-generic package removed and then when I want to reinstall the nvidia drivers it installs the *-386 kernel with it's restricted module. Is there any reason the nvidia drivers will want to install the 386 instead of sticking with the generic?

Thanks!

---

