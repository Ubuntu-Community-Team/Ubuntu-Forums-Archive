---
title: "Need help with Nvidia drivers."
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by ultim_8 on 2008-10-14
I'm trying to setup an older but powerful PC. The Nvidia restricted driver basically locks up x... I'm running a Dell Precision 650 Dual 2.8 Xeon, 2 gigs ram, SCSI Raid, and Nvidia Quadro FX 1000. This is somewhat older hardware but the graphics card is listed on Nvidia supported page, which I found here

[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.12/README/appendix-a.html)

I'm using a fresh install of 8.04, I tried envy and then enabled the restricted driver, but I had to copy xorg.conf from the backup to get x to launch again..

My end goal would be to get the 3d functions to work.

Thanks for any advise.
Tim

---

### Post by Stinger on 2008-10-15
Try [EnvyNG]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by ultim_8 on 2008-10-16
I fixed it.. Apparently there was a problem with my monitor, I switched to a widescreen DVI monitor and now the drivers, compiz, and 3d work great!

Thanks

---

