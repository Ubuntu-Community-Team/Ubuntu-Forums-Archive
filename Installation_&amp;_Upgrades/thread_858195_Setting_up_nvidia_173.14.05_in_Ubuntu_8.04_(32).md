---
title: "Setting up nvidia 173.14.05 in Ubuntu 8.04 (32)"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by rlj1965 on 2008-07-13
Hi,

After using EnvyNG to install the new nVidia graphics driver (173.14.05), I get the following error in Ubuntu 8.04 (32):

--------------------------------------------------------
sudo dpkg --configure -a
Setting up nvidia-new-kernel-source-envy (173.14.05+2.6.24.501-501.30) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
Doing initial module build
Installing initial module
Warning! Cannot do version sanity checking because multiple nvidia.ko
modules were found in kernel 2.6.24-19-generic.
Done.

Setting up nvidia-glx-new-envy (173.14.05+2.6.24.501-501.30) ...

Setting up nvidia-glx-new-dev-envy (173.14.05+2.6.24.501-501.30) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
--------------------------------------------------------------

Is there a way to clear out the old modules so that I can configure correctly?

---

