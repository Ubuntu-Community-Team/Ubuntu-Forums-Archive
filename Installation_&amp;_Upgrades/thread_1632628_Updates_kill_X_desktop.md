---
title: "Updates kill X desktop"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by old_salt on 2010-11-28
I've been experiencing the same issue now for the past several versions. Whenever I perform an update that includes a kernel or kernel library update, I lose the GUI after the update has been performed.

I get the console recovery prompts and after trying everything, nothing works to recover the desktop. It's happened on both Gnome and KDE on different systems, in particular; laptops. 

Very Annoying and I usually have to reload my PC. Anyone experience the same thing?

Just wondering if the Devs are aware of this or not.

---

### Post by sikander3786 on 2010-11-28
I have been installing all of the updates as soon as they are available and never had an issue. In fact, most of the users install the updates and errors are not reported too often. However, I agree there have been some problems though.

Please provide your hardware details and your install setup. Is Ubuntu installed inside Windows using the Wubi installer or on its own separate partition?

Which graphics card is there? And which version of Ubuntu?

---

### Post by old_salt on 2010-11-29
I usually install updates when they are available as well. Just every time there's a kernel update involved, if it doesn't have all 3 associated kernel files, then it bombs on me for some reason. It's once a version run and I always forget to decline the kernel update until I see the 3 files until after the fact. I install the updates and then when I reboot, I end up with the X desktop recovery prompts to reconfigure, repair or manually reconfig the desktiop.

HP Pavilion DV9000 series laptop.
AMD64 - 2.2Ghz Turion
2Gb RAM
nVidia chipset (Graphics, features, modem, NIC, SD Card Reader, etc.)
Broadcom Wireless
Webcam
Lightscribe Matsushita DVD/RW

Win7 and Kubuntu 10.10 64 bit installed in Dual-Boot setup. (Installed Windows then installed Linux).

---

### Post by sikander3786 on 2010-11-30
Are proprietary drivers for Nvidia installed? And if yes, did you install them from the repositories or downloaded them from Nvidia website?

If you installed the .run package fro Nvidia, you may need to recompile the Nvidia module on every kernel upgrade.

And what happens if you choose the older kernel from Grub menu?

---

### Post by tommcd on 2010-11-30
> **old_salt said:**
> 
nVidia chipset (Graphics, features, modem, NIC, SD Card Reader, etc.)

If you installed the nvidia driver from nvidia.com, you will need to reinstall that whenever there is a kernel update. If you had installed the nvidia driver from the Ubuntu repos, the nvidia driver would be automatically reinstalled whenever there is a kernel update for Ubuntu.

---

