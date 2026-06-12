---
title: "X server fails after 10.10 upgrade"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Jasemps on 2010-10-16
Hi all

After performing the 10.10 upgrade I now only get a terminal login. Using the recovery console to enter a failsafe graphic mode works but I cant seem to get the Xserver to run the Nvidia drivers.  The excerpt below is the relevant part of the log file.


[    28.089] (II) LoadModule: "nvidia"
[    28.194] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    28.345] dlopen: /usr/lib/xorg/modules/drivers/nvidia_drv.so: undefined symbol: miEmptyData
[    28.435] (EE) Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    28.435] (II) UnloadModule: "nvidia"
[    28.435] (EE) Failed to load module "nvidia" (loader failed, 7)
[    28.435] (EE) No drivers available.
[    28.435] 
Fatal server error:
[    28.435] no screens found
[    28.435] 

Any assistance would be appreciated.

---

