---
title: "unable to install nVidia 8800 driver"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by bgoedel on 2008-11-29
When running ubuntu 8.10 on my PC the graphics adapter becomes quite hot. If I reboot Windows XP immediately after having ubuntu shut down, it shows 73 degree Celsius. It is a nVidia 8800 GTS card on a 1920x1200 screen.

For Windows XP I have a driver installed that can control the fan in relation to the heat dissipation. I hoped to have a similar feature under ubuntu as soon as I manage to install the driver.

Anyway, I'm unable to install this driver as it won't compile the kernel module. Please find the log the nVidia script produced in the attachment.

I'm running kernel version 2.6.27-9 and have installed (hopefully) all source, header and dev packages for this version of the kernel.

I hope you can help me out of this...

Thanks in advance,
Bernhard

---

### Post by lemming465 on 2008-12-01
The error messages in the log look like that Nvidia driver isn't ported to 2.6.27 yet.  Maybe downgrade to 2.6.24 (hardy kernel) or wait for Nvidia to catch up.  I don't know if they have a beta driver you could try yet, or not.

---

