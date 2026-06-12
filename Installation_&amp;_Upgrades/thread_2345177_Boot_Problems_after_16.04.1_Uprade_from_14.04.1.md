---
title: "Boot Problems after 16.04.1 Uprade from 14.04.1"
date: 2016-12-01
forum: Installation &amp; Upgrades
---

### Post by PaulRSte on 2016-12-01
This is standard Ubuntu with mythtv installed on top. It is built with Raid 1 (Mirror) on most of the partitions except for the mythtv recordings. Unfortunately I had forgotten that an install of mythtvexport had failed some time ago. The upgrade failed at this point and the system will no longer boot on the generic version of the kernel. It stops when the ubuntu screen is displayed with the red dots underneath it.   I have to select the upstart version from the grub menu to get it to boot.  The kernel version upgraded to was 4.4.0-47 from a recently updated version 4.4.0-45. The system had been rebooted on the latter version but again will now only boot from the upstart version of this. The same goes for the previous kernel 4.4.0-42. There was a kernel update yesterday to 4.4.0-51 but this again stops and I have to manually select the upstart version for it to boot ok.

The rest of the upgrade seemed to complete ok in the background except that the mythtv backend no longer auto starts and I've lost the mythtv front end icon from the unity sidebar.  The system is also very slow to boot up. I have also deleted mythtvexport with synaptic package manager.

The main issue is getting the system to boot by itself but it's knowing where to start from, i.e. is this a result of the upgrade crashing part way through or is it just a general issue with this particular upgrade process.

Can anyone help please?

---

