---
title: "Can't install kernel 6.8.0-44-generic upon upgrade from 22.04 to 24.04"
date: 2024-09-17
forum: Installation &amp; Upgrades
---

### Post by design-klipart on 2024-09-17
[COLOR=#000000]Hi Community.[/COLOR]
[COLOR=#000000]I have ran into a problem, during dist upgrade ui tool stuck on grub update.[/COLOR]
[COLOR=#000000]I have ran sudo apt --fix-broken install and it fixed quite a lot of things but now the system is stuck on installing kernel 6.8.0-44-generic.[/COLOR]
[COLOR=#000000]It's quite an old laptop uses ralink bt and wifi adapter and dpkg can't find package for rt3290sta.[/COLOR]
[COLOR=#000000]Hope someone can point me in the right direction what to do here.[/COLOR]

[COLOR=#000000]While running sudo apt --fix-broken install i get:

```

[/COLOR]Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libilmbase25 libmpdec3 libopencolorio1v5 libopenexr25 libpython3.10 libpython3.10-minimal libpython3.10-stdlib libraw20 libtinyxml2.6.2v5 libyaml-cpp0.7
  linux-headers-6.8.0-44 linux-headers-6.8.0-44-generic linux-image-6.8.0-44-generic linux-modules-6.8.0-44-generic linux-modules-extra-6.8.0-44-generic
  linux-tools-6.8.0-44 linux-tools-6.8.0-44-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-6.8.0-45-generic (6.8.0-45.45) ...
Setting up linux-headers-6.8.0-45-generic (6.8.0-45.45) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-45-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
applying patch rt3290sta.patch...patching file src/include/os/rt_linux.h
patching file src/Makefile
patching file src/os/linux/config.mk
patching file src/os/linux/Makefile.6
patching file src/os/linux/Makefile.clean
patching file src/os/linux/pci_main_dev.c
patching file src/os/linux/rt_linux.c
patching file src/tools/Makefile




Building module:
Cleaning build area...
make -j4 KERNELRELEASE=6.8.0-45-generic -C src/ LINUX_SRC=/lib/modules/6.8.0-45-generic/build...(bad exit status: 2)
ERROR (dkms apport): binary package for rt3290sta: 2.6.0.0 not found
Error! Bad return status for module build on kernel: 6.8.0-45-generic (x86_64)
Consult /var/lib/dkms/rt3290sta/2.6.0.0/build/make.log for more information.
dkms autoinstall on 6.8.0-45-generic/x86_64 failed for rt3290sta(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-45-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.8.0-45-generic (--configure):
 installed linux-headers-6.8.0-45-generic package post-installation script subprocess returned error exit status 11
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-6.8.0-45-generic; however:
  Package linux-headers-6.8.0-45-generic is not configured yet.


dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Setting up linux-image-6.8.0-44-generic (6.8.0-44.44
) ...
I: /boot/initrd.img.old is now a symlink to initrd.img-6.8.0-44-generic
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 6.8.0-45.45); however:
  Package linux-headers-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Processing triggers for linux-image-6.8.0-45-generic
 (6.8.0-45.45) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-45-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
applying patch rt3290sta.patch...patching file src/include/os/rt_linux.h
patching file src/Makefile
patching file src/os/linux/config.mk
patching file src/os/linux/Makefile.6
patching file src/os/linux/Makefile.clean
patching file src/os/linux/pci_main_dev.c
patching file src/os/linux/rt_linux.c
patching file src/tools/Makefile




Building module:
Cleaning build area...
make -j4 KERNELRELEASE=6.8.0-45-generic -C src/ LINUX_SRC=/lib/modules/6.8.0-45-generic/build...(bad exit status: 2)
ERROR (dkms apport): binary package for rt3290sta: 2.6.0.0 not found
Error! Bad return status for module build on kernel: 6.8.0-45-generic (x86_64)
Consult /var/lib/dkms/rt3290sta/2.6.0.0/build/make.log for more information.
dkms autoinstall on 6.8.0-45-generic/x86_64 failed for rt3290sta(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-45-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-45-generic (--configure):
 installed linux-image-6.8.0-45-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports has already been reached
                                                                    Processing triggers for linux-image-6.8.0-44-generic (6.8.0-44.44) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.8.0-44-generic
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
Deprecated feature: REMAKE_INITRD (/etc/dkms/framework.conf)
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der
Deprecated feature: REMAKE_INITRD (/var/lib/dkms/rt3290sta/2.6.0.0/source/dkms.conf)
applying patch rt3290sta.patch...patching file src/include/os/rt_linux.h
patching file src/Makefile
patching file src/os/linux/config.mk
patching file src/os/linux/Makefile.6
patching file src/os/linux/Makefile.clean
patching file src/os/linux/pci_main_dev.c
patching file src/os/linux/rt_linux.c
patching file src/tools/Makefile




Building module:
Cleaning build area...
make -j4 KERNELRELEASE=6.8.0-44-generic -C src/ LINUX_SRC=/lib/modules/6.8.0-44-generic/build...(bad exit status: 2)
ERROR (dkms apport): binary package for rt3290sta: 2.6.0.0 not found
Error! Bad return status for module build on kernel: 6.8.0-44-generic (x86_64)
Consult /var/lib/dkms/rt3290sta/2.6.0.0/build/make.log for more information.
dkms autoinstall on 6.8.0-44-generic/x86_64 failed for rt3290sta(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.8.0-44-generic
   ...fail!
run-parts: /etc/kernel/postinst.d/dkms exited with return code 11
dpkg: error processing package linux-image-6.8.0-44-generic (--configure):
 installed linux-image-6.8.0-44-generic package post-installation script subprocess returned error exit status 11
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-headers-6.8.0-45-generic
 linux-headers-generic
 linux-generic
 linux-image-6.8.0-45-generic
 linux-image-6.8.0-44-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


[COLOR=#000000]
```
[/COLOR]

---

