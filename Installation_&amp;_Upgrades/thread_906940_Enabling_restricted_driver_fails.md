---
title: "Enabling restricted driver fails"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by rocketssss on 2008-09-01
I just installed Xubuntu on a pentium 4 Dell machine and the system informs me I can enable an NVIDIA driver to enable 3D acceleration, which I want to do. When I try to update, I get the error:

> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx_96.43.05+2.6.24.13-18.41_i386.deb)
   404 Not Found

Browsing to this URL in firefox shows it's obviously non-existent. There is a huge list of files, but I don't know which to use, or how to install it manually. Any ideas?

Thanks! :)

---

### Post by Partyboi2 on 2008-09-01
Try reloading the package infomation. Open a terminal and```
 sudo apt-get update
``` then try installing the driver again.

Edit: If that does not work download the package from [[COLOR=Blue]here[/COLOR]]("http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-dev_96.43.05+2.6.24.14-21.48_i386.deb") and double click to install.

---

### Post by Bucky Ball on 2008-09-01
I had a similar problem recently. My nvidia driver in Hardware Devices was saying ticked/installed but not in use. I unticked it, shut the window, opened up again, ticked it, downloaded the driver (nvidia-glx-new), asked for a restart and there you go. Worked for me.

In effect, this is what Partyboi is saying to do but through GUI (System->Administration->Hardware Drivers).

(ps: Partyboi2, no offence, but that is one freakish baby with a face only a mother could love ... but kinda cute all the same! hahaha)

---

