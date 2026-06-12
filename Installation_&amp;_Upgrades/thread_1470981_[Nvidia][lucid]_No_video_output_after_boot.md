---
title: "[Nvidia][lucid] No video output after boot"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Man of Wax on 2010-05-03
Hi,
It's 3 days I'm trying to solve this bug:
[https://bugs.launchpad.net/ubuntu/+bug/573837](https://bugs.launchpad.net/ubuntu/+bug/573837)

As you can read on launchpad in my last test I've tried to disable nvidia driver but the driver manager completly deleteted it. Now I've reinstalled the nvidia driver and with the kernel .32 my computer dies as usual. 
With kernel .31 the "Monitor Settings" and "Driver Manager" say the nvidia driver is installed but the Nvidia-Settings says the driver is NOT installed. In fact if I try to generate a Xorg.conf with nvidia-xconfig the X Server doesn't find any "nvidia" modules.

So now my situation is worse than yesterday: with kernel .32 and Nvidia I got no video output and the system seems in kernel panic (same as yesterday), without Nvidia drivers my screen max resolution is 1280x1024 instead of 2048x1152 so I can barely use it for very quick test before my eyes start to hurt (same as yesterday) and now with kernel .31 I can't get Nvidia drivers working at all.

---

### Post by Man of Wax on 2010-05-04
Some news:
Today I've reinstalled Ubuntu 10.04.
With "quite splash" the nouveau doesn't work and the system freeze after grub. With "nomodeset" I can boot but the screen resolution in incorrect. I've tried to install nvidia proprietary drivers but after the reboot the system freeze and I have no video output (the screen goes in power saving mode).

Any help?

---

