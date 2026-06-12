---
title: "Can't get nvidia working"
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by kuleali on 2005-03-19
I upgraded my warty to hoary, but did not upgrade to the lastest kernel, because my computer froze when i used those kernels.
I use the 2.6-8-1 k7

when i enable my nvidia card
nvidia-glx-config enable
and change my /etc/x11/xorg.conf. from nv to nvidia then my x will not start. If i change it back again my x start working.

But i need my video card. 

Any solution on how i can get my onboard nvidia geforece 4mx to work?

i get this massage from x

The Nvidia kernel module is version 1.0.6111
X module is v 1.0.6629

make shure they are the same.

But in synaptic it shows me that i have nvidia kernel module v 1.0.6629 ?

---

### Post by jnow on 2005-03-20
the same as you
and when i used kernel 2.6.10 or 2.6.8 
the "nvidia" did not work
i had to use "vesa"

---

### Post by mmealman on 2005-03-20
[QUOTE=kuleali]I upgraded my warty to hoary, but did not upgrade to the lastest kernel, because my computer froze when i used those kernels.
I use the 2.6-8-1 k7

when i enable my nvidia card
nvidia-glx-config enable
and change my /etc/x11/xorg.conf. from nv to nvidia then my x will not start. If i change it back again my x start working.

But i need my video card. 

Any solution on how i can get my onboard nvidia geforece 4mx to work?

i get this massage from x

The Nvidia kernel module is version 1.0.6111
X module is v 1.0.6629

make shure they are the same.

But in synaptic it shows me that i have nvidia kernel module v 1.0.6629 ?[/QUOTE]
 Nvidia has 2 parts, the kernel module and the GLX libraries. The 2.6.10 restricted modules have the 6229 nvidia driver while the 2.6.8 kernel has the 6111 one. Make sure you're using the proper GLX package "dpkg --list | grep nvidia-glx" will show you which one you're using.

---

### Post by gnutux on 2005-03-20
Please use the latest driver: 1.0-7176

The cause of this problem is because your newly updated kernel no longer has the drivers since the drivers are patched into the kernel itself. You must reinstall the driver whenever you update your kernel.

gnutux

---

