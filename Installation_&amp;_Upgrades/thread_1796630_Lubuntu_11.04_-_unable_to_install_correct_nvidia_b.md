---
title: "Lubuntu 11.04 - unable to install correct nvidia binary driver"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by raenur on 2011-07-04
I had slightly annoying night trying to get the right nvidia drivers loaded on an old XC cube system I have with a Geforce 4 MX chipset. The nouveau driver doesn't work very well for the hardware, and installing nvidia-current is no use as the driver doesn't find any suitable devices, but trying to install the nvidia-96 package results in the package manager trying to remove the lubuntu core system and a lot of xorg packages. I haven't had any luck installing the driver packages obtained direct from nvidia.

Is this some dependency confusion or am I going about things in the wrong way?

---

### Post by JC Cheloven on 2011-07-07
> **raenur said:**
> ... but trying to install the nvidia-96 package results in the package manager trying to remove the lubuntu core system and a lot of xorg packages.

If what you see is that "lubuntu desktop" will be removed, don't worry, it's not the "core system", but only a meta-package that is removed as soon as any of its dependencies is removed. Won't realy affect anything installed. Have a look on [this]("http://lubuntu.net/blog/lubuntu-screencast-metapackages-detail").

---

### Post by tommcd on 2011-07-08
Unfortunately, the nvidia-96 driver is known to be problematic on Ubuntu 11.04: 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/741930](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/741930)
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/790660](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/790660)
[http://www.linuxquestions.org/questions/ubuntu-63/nvidia-96-series-drivers-for-ubuntu-11-04-a-879438/](http://www.linuxquestions.org/questions/ubuntu-63/nvidia-96-series-drivers-for-ubuntu-11-04-a-879438/)

---

