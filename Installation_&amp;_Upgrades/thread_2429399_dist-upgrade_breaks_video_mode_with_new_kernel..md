---
title: "dist-upgrade breaks video mode with new kernel."
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by JohnnyS987 on 2019-10-17
I have an NVidia vid card, and I have a problem every time I do a dist-upgrade and the kernel gets upgraded. I lose my multi-monitor configuration and the resolution changes to a low-res mode.

I can "fix" this as follows:

1. Open Settings 
2. Select "Additional Drivers" 
3. Set video mode to "Using X.Org X Server -- Nouveau display driver from xserver-xorg-video-nouveau (open source) and wait for it to install.
4. Reboot.
5. Open Settings 
6. Select "Additional Drivers" 
7. Set video mode to "Using NVIDIA driver metapackage from nvidia-driver-418 (proprietary, tested)" and wait for it to install.
8. Reboot AGAIN.

It's a repeatable process, but how can I do this from the CLI? That would be much easier and faster. What commands are being run by the GUI tools?

---

