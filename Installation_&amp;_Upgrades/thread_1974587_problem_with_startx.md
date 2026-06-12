---
title: "problem with startx"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by kospanak on 2012-05-06
hello to all ubuntu users

i have a small problem. I just installed Ubuntu 12.04. Since then every time i start the computer, it always stucks on Power checking. Then i press Alt-F4 and i get into the command-line. When i type startx i get this message:

"Default Screen Section" for depth/fbbpp 24/32
[    57.107] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    57.107] (==) NVIDIA(0): RGB weight 888
[    57.107] (==) NVIDIA(0): Default visual is TrueColor
[    57.107] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    57.108] (**) NVIDIA(0): Enabling 2D acceleration
[    57.565] (EE) NVIDIA(GPU-0): The NVIDIA GPU at PCI:1:0:0 does not have the necessary
[    57.572] (EE) NVIDIA(GPU-0):     external power cables attached; X cannot use this GPU
[    57.572] (EE) NVIDIA(GPU-0):     until the problem is rectified.  Please shut down your
[    57.572] (EE) NVIDIA(GPU-0):     computer, open its case, and attach all of the appropriate
[    57.572] (EE) NVIDIA(GPU-0):     power connectors.  Please see the documentation provided
[    57.572] (EE) NVIDIA(GPU-0):     with your NVIDIA GPU for more details.
[    57.909] (II) UnloadModule: "nvidia"
[    57.909] (II) Unloading nvidia
[    57.909] (II) UnloadModule: "wfb"
[    57.909] (II) Unloading wfb
[    57.909] (II) UnloadModule: "fb"
[    57.909] (II) Unloading fb
[    57.909] (EE) Screen(s) found, but none have a usable configuration.
[    57.909] 
Fatal server error:
[    57.909] no screens found
[    57.909] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    57.909] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    57.909] 
[    58.047]  ddxSigGiveUp: Closing log
[    58.047] Server terminated with error (1). Closing log file.

and i cann't get in Desktop. But there is no problem when i use the ubuntu CD to get into the desktop, when i want to try ubuntu.

What could be the problem?

---

### Post by SeijiSensei on 2012-05-06
Sure looks like a hardware problem.  Try opening the case and removing and reseating the video card with the NVIDIA chip.

---

