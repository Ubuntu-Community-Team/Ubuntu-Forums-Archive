---
title: "Don't upgrade or install Ubuntu 8.04 to a partition exceeding partition number 15"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by Marlo_nl on 2008-07-07
Warning: Don't upgrade or install Ubuntu 8.04 to a partition exceeding partition number 15.


I've tried to do this myself, only to come to the very disappointing conclusion:

Upgrading from Ubuntu 7.10 (Gutsy Gibbon) to Ubuntu 8.04 (Hardy Heron) does not work for my system.


Booting from the Unbuntu 8.04 LiveCD is OK, but trying to install (instead of upgrading) Ubuntu using the LiveCD doesn't work either.

Booting from the Ubuntu 8.04 LiveCD and checking my (PATA) HDD partitions using GPARTED gives the following:

"The kernel is unable to re-read the partition tables from the following devices:
- /dev/sda"

Remark: partitions sda1 up to sda15 appear correctly in GPARTED, partitions sda16 and higher are not OK (exclamation mark)


When booting from the Ubuntu 7.10 LiveCD and checking my HDD partitions using GPARTED, all partitions appear OK.

Note: in Ubuntu 7.10 my PATA IDE HDD partitions are identified by /dev/hda (not sda).



My preliminary conclusion is (please correct me if I'm wrong): 

The kernel used in Ubuntu 8.04 is not backwards compatible with the Ubuntu 7.10 kernel. 
The Ubuntu 7.10 kernel supports up to 63 partitions on an IDE disk, the Unbuntu 8.04 kernel will only support up to 15 partitions (it will treat the IDE disk as a SCSI disk) 


I understand that this incompatibility will only affect a small percentage of the total Ubuntu population.
Only those who have organized their HDD to have a large number of partitions might suffer from the incompatibility.

Still, I would think that any backwards compatibility issue is important enough to be mentioned somewhere.

The System Requirements Section on [http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition](http://www.ubuntu.com/products/WhatIsUbuntu/desktopedition) does not mention a change in supported number of HDD partitions. Nor did I find a clear statement related to a change in HDD requirements in other Ubuntu 8.04 documentation.

Suggestion to Canonical:
Maybe it is a good idea to document the requirement change related to HDD partitions somewhere. 
It might help other Ubuntu  users who have encountered problems in upgrading/installing Ubuntu 8.04 in finding the root cause. 
Or even better, it might help other Ubuntu users to decide not to upgrade/install Ubuntu 8.04 in case their systems are not in line with the Ubuntu System Requirements.


I hope this thread helps others who are struggling with the Ubuntu 8.04 upgrade or installation.

If anyone encountered similar problems and found a solution (other than HDD repartitioning) I would be interested it learn about this.


Regards,

Marlo

---

