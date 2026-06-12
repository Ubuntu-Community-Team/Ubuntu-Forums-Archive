---
title: "Ubuntu won't boot after updating 12.04"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by therother on 2014-04-15
I've just updated my server's 12.04 installation from 3.2.0-36 to 3.2.0-60.  Everything appeared to go ok until the reboot.  This is what it says:

[ATTACH=CONFIG]252092[/ATTACH]

The system boots ok when I select 3.2.0-36 under the previous linux versions in grub.  It seems to function ok for now but apt is full of errors.  There are 4 disks in the machine as well as the boot disk. The boot disk is sdd under 3.2.0-36 but 3.2.0-60 seems to be looking for sde. In 36, sda and sdb are 3TB disks and sdc is a 6TB raid0 created using the motherboard's onboard RAID controller. Is it possible that 60 is now seeing the raid0 are two disks and this is my problem?

I'm was about to upgrade to 14.04 anyway, and all the data is mirrored daily to the attached NAS, so I'm not adverse to a clean 14.04 install but was wondering if there was a quick fix?

---

