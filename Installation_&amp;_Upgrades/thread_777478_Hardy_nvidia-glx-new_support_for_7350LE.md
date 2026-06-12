---
title: "Hardy nvidia-glx-new support for 7350LE ?"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by m.letcher on 2008-05-01
Updated to Hardy 8.04. I appear to have have lost support from the restricted glx driver with the shift to glx-new for this video card ( NV-7350LE ) which used to work fine with glx. I looked through the supported hardware list and it appears to have been dropped.

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)
doesn't show support for device ID=0x01D0. I've flailed around a bit with the nv driver 169.12, envyng, shifting back to nvidia-glx, etc but can't seem to get more than VESA support for the 1440x900-wide monitor. 

This is a bit of a surprise since the Gutsy and Feisty releases didn't have this issue.

Will this graphic card be supported in the future ?

---

### Post by m.letcher on 2008-05-01
I found that Nvidia has a 173.08 Beta driver which does include the 7350LE as supported via the Readme link.

Version: 173.08
Operating System: Linux x86
Release Date: April 10, 2008 
[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

[http://us.download.nvidia.com/XFree86/Linux-x86/173.08/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.08/README/appendix-a.html)

However, I haven't got this driver to install itself after executing the .run pkg.

Ubuntu likely won't support a beta driver in any event, though there are comments about fixes being made to support the 2.6 kernels.
"Restored compatibility with recent Linux 2.6 kernels."

---

