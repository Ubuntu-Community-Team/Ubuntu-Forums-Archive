---
title: "[Heron] Nvidia/Xorg problems, glx not working"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Sam Liu on 2008-04-26
Whenever I use envy to install nvidia-glx-new and all the other drivers and stuff, my computer boots into low graphics mode and if I ctrl+alt+backspace and hit startx it gives me an error.

I looked in the logs and it shows this:
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Also the error given talked about my nvidia kernel and driver versions not matching. How would I solve that? I already tried purging envyng and the nvidia drivers and reinstalling. I also tried installing legacy drivers but that screws up the resolution anyway...


//solved
okay I fixed it by manually compiling and installing the driver.. =___=

---

