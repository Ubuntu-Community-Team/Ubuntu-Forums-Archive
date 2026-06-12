---
title: "9800 GTX+ NVIDIA NOUVEAU don't work anymore in 10.10"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by mietzekater on 2010-11-16
Hi,...

since today my ubuntu 10.10 boots only into console, no GUI anymore. The only solution to start gdm is to load vesa drivers in xorg.conf. 

Kernel is 2.6.35-23-generic

The Xorg.0.log:
(EE) [drm] failed to open device
(EE) No devices detected.

I googled a lot but nothing really helps so far...

What can I do and which information could help you to find the error?

---

### Post by gabouel on 2010-11-28
Hi, I am having the same issue on my VAIO laptop (NVidia 330M).

Tried to install the NVidia proprietary driver and hangs after "Checking Battery state" without even letting me access any tty.
Nothing in the logs.

At this point, only the "nv" driver works but I am missing compositing quite a lot.

Also tried to uninstall nvidia*, reinstall libl1.mesa stuff, xorg, install NVidia proprietary driver again without any success.

Any help would be very appreciated.

EDIT:
Finally managed to get a working NVidia Proprietary driver. I had to switch back to the version 256.53.

[The driver can be found here (64bits version)]("http://www.nvidia.co.uk/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/256.53/NVIDIA-Linux-x86_64-256.53.run&lang=uk&type=GeForce")

---

