---
title: "Help please! cannot install wireless driver for Broadcom 4312"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by Xxjmoxx on 2011-10-17
root@ubuntu:~# apt-get --reinstall install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 37 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu4) ...
Removing old bcmwl-5.100.82.38+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.38+bdcom
Kernel:  3.0.0-12-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod........(bad exit status: 135)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 5.100.82.38+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture x86_64
Building initial module for 3.0.0-12-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod........(bad exit status: 135)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 5.100.82.38+bdcom
Kernel:  3.0.0-12-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.0.0-12-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........(bad exit status: 135)

DKMS: uninstall Completed.
Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

