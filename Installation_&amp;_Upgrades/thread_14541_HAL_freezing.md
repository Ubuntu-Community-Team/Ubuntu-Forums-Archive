---
title: "HAL freezing"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by adamslade on 2005-02-08
HELP... Would love to enjoy the world of Ubuntu, if I could get chance to learn it  #-o  (At the moment I don't even think I could describe myself as a begineer!!)


The only way I can get through the installation is to choose Custom mode and do a minimal install.  Everything appears to be fine under normal install except that it freezes moments after the Hardware Abstraction Layer (HAL) is started.

I have tried boot parameters pci=noacpi, noapic, and nolapic in combination and still no joy.

Having done a custom minimal installation, if the first thing I install is the basic HAL pacakge, again as soon as the HAL is started...frozen  :sad: 

I'm not sure if the following errors are connected having read the forums they don't seem to be, in fact they don't seem important, but just in case.

-------------
*Starting hotplug subsystem...
 modprobe: FATAL: Error inserting hw_random (/lib/modules/2.6.8.1-3-386/kernel/drivers/char/hw_random.ko): No such device
 modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/pciehp.ko): Operation not permitted
 modprobe: FATAL: Error inserting shpchp (/lib/modules/2.6.8.1-3-386/kernel/drivers/pci/hotplug/shpchp.ko): Operation not permitted
-------------

Hardware is HP Compaq Laptop NX5000.

---

