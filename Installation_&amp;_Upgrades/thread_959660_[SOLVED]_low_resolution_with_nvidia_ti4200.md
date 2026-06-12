---
title: "[SOLVED] low resolution with nvidia ti4200"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by sete15 on 2008-10-26
Hi

I have installed Hardy heron and after i managed to download all the updates i decided to enable the restricted drivers for the Nvidia GeForce 4 TI4200 with AGP 8X that i have as a video card.
When finished downloading the glx driver the system asked me for reboot and then the resolution went to 640x450.As there are no higher resolutions available in the settings, what i have to do to go again to 1024 x 768 that i had before enabling also and the visual effects?
P.

---

### Post by Partyboi2 on 2008-10-26
Try adjusting your resolution in nvidia-settings (System>Admin>Nvidia Settings) if you can not find nvidia settings under System>Admin then you can install it by synaptic or by terminal
```
sudo apt-get install nvidia-settings
```

---

### Post by sete15 on 2008-10-27
Thanks for your help,i managed to have the nvidia x-server available but there is not available any resolution settings and the resolution is stuck to 640 X 350 @70HZ.Is there any other step that i have to do?

---

