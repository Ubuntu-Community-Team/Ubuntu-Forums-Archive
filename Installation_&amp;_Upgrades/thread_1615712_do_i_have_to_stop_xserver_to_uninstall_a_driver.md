---
title: "do i have to stop xserver to uninstall a driver ?"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2010-11-07
i installed a nvidia graphics driver while stopping xserver
because ubuntu hardware drivers wizard would not let me install from gui


i want to upgrade to latest ubuntu but i read on this site that its best not to have old driver when updating


will the latest ubuntu recognise my ddr5 geforce gt 240 ?

---

### Post by dino99 on 2010-11-07
actual distro and kernel directly deals with X, so dont worry. You can check your driver activation (system admin additional driver), you might have nvidia-current activated

the easiest way to install: use synaptic and search "nvidia"

---

### Post by jimbean on 2010-11-07
your above my head with that answer
does your answer mean 
just to do upgrade without worries from nvidia driver

---

### Post by Frogs Hair on 2010-11-07
Many packages will be automatically removed and / or replaced during the upgrade including the driver . You can remove the Nvidia driver with Synaptic Package Manager or the Additional Drivers Jockey prior to upgrade if you like without need of stopping Xserver. I would be concerned about the fact that you were unable to install the driver using the jockey .

---

