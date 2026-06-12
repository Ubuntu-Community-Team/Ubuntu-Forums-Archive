---
title: "install/rescue with network card not directly supported"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by msz on 2012-10-25
I have a problem with installing and, even worse, booting "rescue" option from 12.04 AMD64 Server install CD.

My systems are SuperMicro blades equipped with Mellanox 10GbE/Infiniband network controllers. The proper drivers for them are 'mlx4_core' (common base for both 10GbE and IB use) and 'mlx4_en' on top of it, to select 10GbE ethernet mode.

When booting for the installation media, only 'mlx4_core' is loaded so the installer does not see the ethN interface. Still, I was able to install in local mode, just cancelling some netwrok-related activities during the process. Once installed, I was able to add 'mlx4_en' driver to the configuration and it is working. 

I would prefer, however, to be able to somehow teach the installer to use the proper driver.

Even worse situation happens when I boot to 'rescue system' option from the installation CD. No 'mlx4_*' driver is available in this mode.

any hints would be appreciated
regards, Michal.

---

### Post by dino99 on 2012-10-25
on desktop QQ installation we have libmlx4-1 as driver and ibutils for testing

---

