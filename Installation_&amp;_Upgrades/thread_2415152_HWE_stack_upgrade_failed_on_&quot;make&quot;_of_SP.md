---
title: "HWE stack upgrade failed on &quot;make&quot; of SPL package of ZFS 0.7.5."
date: 2019-03-21
forum: Installation &amp; Upgrades
---

### Post by lammert-nijhof on 2019-03-21
My HW stack upgrade failed, because zfs 0.7.5 had not been updated to zfs 0.7.9 during the HWE stack upgrade. If you download the 18.04.2 ISO image you get ZFS version 0.7.9. Now the upgrade failed on the "make" of SPL (ZFS package). Afterwards the system did not boot anymore and I had to restore the system from a backup. I have filed a bug-report on the 17th of February, but there is absolutely no action on it, there is no responsibility nor priority assigned to the bug report. 

The only work-around I know, is to re-install the system from scratch using the ISO file with the correct ZFS version, either Ubuntu 18.04.2 or maybe even Ubuntu 19.04. That re-installation is somewhat complex, since I boot from ZFS and I have to install to e.g. a ext4 partition and afterwards move that installation to the ZFS dataset. That upgrade to Linux 4.18 is important, since I'm building a Ryzen 3 2200G system. I want to move SSD and HDDs "as-is" to the new system (4-core Phenom II to 4-core Ryzen 3). However it seems, I have to move to at least Linux 4.18 to get some support for the VEGA 8 integrated GPU. 

Does anyone has a suggestion how to update the HWE stack e.g. step by step or how to install a newer ZFS version before the HWE upgrade? 
Another alternative is to install Ubuntu 19.04 with Linux 5.0. 
- Any experience with that 19.04 system and ZFS? In Virtualbox it seems to work with the Ubuntu version of ZFS 0.7.12. 
 - Will ZFS 0.8 be supported by Ubuntu 19.04?
- Any experience with 18.04.2 system or the 19.04 system and the Ryzen 3 2200G?

---

