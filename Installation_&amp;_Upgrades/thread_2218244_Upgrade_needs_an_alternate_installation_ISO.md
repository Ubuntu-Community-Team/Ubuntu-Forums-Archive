---
title: "Upgrade needs an alternate installation ISO"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by styx2 on 2014-04-20
14.04 LTS upgrade does not play well with RAID motherboards. I have an Asus SK8V (AMD64) with two drives attached to the onboard VIA Raid controller. Even without a RAID configured the standard installation would only see the two disks as a single RAID disk... and crash with any attempt to install partitions. I finally got 12.04 LTS installed with the alternate installation ISO by selecting NOT to activate the detected RAID drives. Both drives would then be seen and I could install / and /swap on the first drive and /home on the second. SINGLE OS...GRUB installed correctly to SDA and the system is working fine. I was hoping the upgrade would recognize and maintain that configuration. Unfortunately it does not. A Live DVD boot confirms that this version does not see the two drives at all. Attempting a clean installation has the same problem as earlier versions reporting the two drives as a single double sized drive with incorrect dev id's/UUID's. The upgrade crashes at the reboot as GRUB fails to see the old drive (the UUID it is looking for is correct - I confirmed the UUID prior to upgrading - but in this version it can't see the drive itself). Guess I'm stuck at 12.04 until an alternate installation ISO appears for this version. :(

---

### Post by styx2 on 2014-04-20
Ah... The unrelated posts you discover that solve your problems...

I just booted the Live DVD hitting F1 at the initial splash screen. Choosing F6 and then "nodmraid" allowed the desktop to see all of my drives. I will either try to upgrade with that parameter or more likely do a fresh install. Will report back.

---

### Post by styx2 on 2014-04-20
Nope.... 

Still get:

Alert! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist.  Dropping to a shell!

---

