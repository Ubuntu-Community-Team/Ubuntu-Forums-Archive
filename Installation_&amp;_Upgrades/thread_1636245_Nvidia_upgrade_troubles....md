---
title: "Nvidia upgrade troubles..."
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by marcusdufrane on 2010-12-02
Ubuntu 8.04
Nvidia GeForce 8400gs

Trying to upgrade my video drivers. The current version I get from the repo is 169.12 and the newest version from Nvidia is 200.19.21.

I have been able to install the drivers just fine. The problem comes at restart. When the computer restarts it is unable to load the driver and gives me th good old configuration bs at startup.

If I stop gdm and install the driver then start gdm everything works just fine. So I need to find out why it doesn't reload after a restart.
I have a feeling it has to do with removing the old drivers that are on here but i wasn't able to figure out how to do that.

any ideas guy?

---

### Post by Frogs Hair on 2010-12-02
To remove the old driver from the menu  System > Administration > Synaptic Package Manager. Use the search filter to locate the driver , right click on that line and mark for complete removal and select apply.

---

### Post by marcusdufrane on 2010-12-02
I have checked through synaptic, and all nvidia devices are unchecked. Except the nvidia common files
and xserver-xorg-video-nv

so it seems that the old drivers are off.

Any ideas as to why it doesn't want to load on reboot?

---

### Post by marcusdufrane on 2010-12-03
Still not able to get the thng to load on boot.

---

