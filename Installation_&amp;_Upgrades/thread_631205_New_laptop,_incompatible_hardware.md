---
title: "New laptop, incompatible hardware"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by xodeus on 2007-12-04
Hi all.
I've just bought a new computer. It's a TOSHIBA Satellite A210-138.
The specs are here:
CPU : 1.6 GHz AMD Turion(tm) 64 X2 Dual-Core TL-52
RAM : 2,048 (1,024 + 1,024) MB DDR2 RAM (667 MHz)
HDD : 120 GB
DVD Super Multi-DL-drive
Screen: 15.4" Toshiba TruBrite® WXGA TFT 1,280 x 800
[COLOR="Sienna"]GFX: ATI Radeon® X1200 up to 831 MB Shared
Network: Atheros 5007EG 802.11 B/G Wi-Fi®[/COLOR]

Now I'm interested, will Ubuntu work on this computer Out Of The Box or do I have to make some changes to get the graphics and wireless working?

---

### Post by Pumalite on 2007-12-04
If you decide to install; do it with the Alternate CD while wired to the Internet. You'll probably have to configure your xserver and wireless after the installation.

---

### Post by Teamgeist on 2007-12-04
For Wireless follow this tutorial:
[http://ubuntuforums.org/showthread.php?p=2688436](http://ubuntuforums.org/showthread.php?p=2688436)
It uses ndiswrapper but works just fine.

Concerning your graphics card I suggest using Envy if you want to use Desktop effects since it will install the very laetst ATI driver for you.

direct download:
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu1_all.deb)

Info on Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good Luck!

---

### Post by xodeus on 2007-12-05
So I need to get ndiswrapper & Envy and all dependencies on my USB Flash, cuase I can't get wired at the place I'm using the computer.

---

### Post by Pumalite on 2007-12-05
Good luck.

---

