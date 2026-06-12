---
title: "Video card not working correctly"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by MartyD82 on 2007-09-10
Hello,

I have recently installed Ubuntu 7.04 on a Xeon 32 bit processor with an NVIDIA Quadro4 980 XGL video card. I have made many attempts at installing my video drivers. The installations were successful. However, when I boot up my system, I receive an error message saying that my video card's "X-server is not configured properly."

Specifically, my  Xorg.0.log.old file shows me this:

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I have tried uninstalling and reinstalling various video drivers, all of which are (according to their corresponding Readme files) compatible with my video card. But nothing seems to work. 

Any suggestions would be greatly appreciated.

---

### Post by Pumalite on 2007-09-10
Delete

---

### Post by MartyD82 on 2007-09-11
Nevermind.

---

