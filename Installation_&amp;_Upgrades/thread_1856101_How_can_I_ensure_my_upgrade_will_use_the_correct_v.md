---
title: "How can I ensure my upgrade will use the correct video drivers on next boot"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by renegadeandy on 2011-10-07
Hey guys. I am upgrading from 10.10 to 11.04 at the moment.

Last time I did an upgrade from 10.04 to 10.10 it overwrote my display driver of choice - and meant X could not start properly and i found it very difficult to fix.

Is there anything I can do before I reboot to complete the upgrade to ensure that my ATI driver is used during the next boot when the upgraded system is loading? 

Thanks,

Andy:popcorn:

---

### Post by MartyBuntu on 2011-10-07
Disable proprietary drivers, then re-enable them after the upgrade.

---

### Post by MAFoElffen on 2011-10-07
> **MartyBuntu said:**
> Disable proprietary drivers, then re-enable them after the upgrade.
Additional to the- 
Update Manager > Settings > Ubuntu Software Tab > "Proprietary drivers for devices (restricted)

[COLOR=Gray]Also located in software sources of Synaptic...[/COLOR]

It will make up a backup copy your xorg.conf file to the /etc/X11 directory in this filename format:
 xorg.conf.date_of_distupgrade ... but I always keep a backup copy of my latest xorg.config in my home directory.

---

