---
title: "dmraid support during install"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by SRParda on 2007-11-19
Hi,

**I would suggest to add dmraid support during installation of Ubuntu 7.10 or next versions. **


It would be important because:
We are computer integrators, and we give the option of Linux install  to our customers. We usually sell the latest technologies and a we always offer motherboards with RAID for enhanced performance and security. 

I know we could install software RAID but the majority of our clients buy and use Windows Vista too, and is necessary to install the motherboard RAID for them. So Linux must use dmraid too. 

That's not problem in Linux, but in Ubuntu 7.10 specifically we are having problems:

- Difficult and tricky installation, because dmraid is not in the official repositories.
- With manual installation (At least in Intel Matrix RAID with an Intel P35 chipset motherboard ) we have suffered corruption of the array using gparted. (Strange because we have installed dmraid with Ubuntu 6.10)


We have tested Fedora, and it works perfect at least in versions 7 and 8. It enabled dmraid during installation, show the RAID volumes and partitions during install  (and excluded the physical units preventing mistakes).


This is not a critic, only a exposition of things, to help developers to make ubuntu better.


Thank You,


PD: We are interested if other persons, use (or are interested in use) raid controllers included in his motherboards with dual SO. You can post here to help developers to consider it..

---

