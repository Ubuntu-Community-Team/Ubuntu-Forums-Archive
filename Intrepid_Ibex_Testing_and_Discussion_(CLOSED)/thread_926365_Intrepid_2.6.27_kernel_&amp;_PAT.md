---
title: "Intrepid 2.6.27 kernel &amp; PAT"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dkasak on 2008-09-21
Hi all.

I have an issue ( hard lockup ) my my video card ( Radeon X700 Mobility ) with Intrepid. I posted details to the Xorg mailing list. I've been asked if I use PAT in my kernel. Do I?

---

### Post by RAOF on 2008-09-21
```
grep PAT /boot/config-2.6.27-3-generic
```
includes 
> 
# CONFIG_X86_PAT is not set

which suggests the answer, at least for the amd64 kernels, is "no".

If you're not using an amd64 kernel, I'd suggest running the command on your system.

Additionally: Have you reported a bug against the driver package on [Launchpad](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+filebug)?  That's generally the best place to start, since the problem may be Ubuntu-specific.  The Ubuntu [X bug reporting guide](https://wiki.ubuntu.com/X/Reporting) might be useful for you.

---

