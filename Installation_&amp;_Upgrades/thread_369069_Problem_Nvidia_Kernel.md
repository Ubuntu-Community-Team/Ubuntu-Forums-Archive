---
title: "Problem Nvidia Kernel"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by sdil on 2007-02-24
I only can use X using Vesa Driver. When I startx using NVIDIA driver, it say cannot load NVidia kernel. Can you help me. I has follow the instruction from this homepage :[http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html) Please Help me  :confused:  :confused:

---

### Post by kerry_s on 2007-02-24
If you followed that no wonder it don't work. You only need to->

sudo apt-get install nvidia-glx
sudo nvidia-xconfig
reboot

that's it.

---

