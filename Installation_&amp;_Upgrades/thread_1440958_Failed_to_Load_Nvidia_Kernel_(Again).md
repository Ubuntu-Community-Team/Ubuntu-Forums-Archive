---
title: "Failed to Load Nvidia Kernel (Again)"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by mac666 on 2010-03-28
Hey

Ive been having this trouble every 20th reboot since i got to ubuntu, but now i cant do anything about it.

```
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Mar 28 13:03:34 NVIDIA(0): Enabling RENDER acceleration
(II) Mar 28 13:03:34 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Mar 28 13:03:34 NVIDIA(0):     enabled.
(EE) Mar 28 13:03:34 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Mar 28 13:03:34 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Mar 28 13:03:34 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
```

Ive been trying to reconfigure the graphics. (remove, create new generic & for My hardware, et c)
Ive been trying to reinstall the nvidia graphic.
I have no trouble booting into "low graphic mode"
Found no clues on the internets.... 

Please? :(
Im on Karmic x64 with latest kernel and NVIDIA-Linux-x86_64-190.32-pkg2 graphic drivers... I will try to use the later nvidia drivers now...

---

### Post by mac666 on 2010-03-28
K i downloaded the latest and Voila! :)

---

