---
title: "Raedon Video Card Drivers"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by Ewpoxy on 2012-06-08
Okay, so I am completely new to Ubuntu, as well as Linux itself. I figured something I should start out with was trying to install video card drivers. My rig currently has two Raedon 7870s with a CF bridge on them. Okay, so I followed a guide on installing video drivers and everything was going good until the finished prompt. 

It said there was a error, and here is the log it gave me.

> 
Uninstalling any previously installed drivers.
Unloading drm module...
ERROR: Module drm is in use by vmwgfx,ttm
[Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.a .??* *.symvers
make -C /lib/modules/3.2.0-23-generic/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/firegl_public.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_acpi.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_agp.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_debug.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_ioctl.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_io.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_pci.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_str.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_iommu.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl.o
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/kcl_wait.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /lib/modules/fglrx/build_mod/2.6.x/fglrx.mod.o
  LD [M]  /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
build succeeded with return value 0
duplicating results into driver repository...
done.
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
- recreating module dependency list
- trying a sample load of the kernel modules
failed.
[Error] Kernel Module : Reboot required. 
[Reboot] Kernel Module : update-initramfs

If anyone could help me, I'd greatly appreciate it. Also if it matters, I'm running inside of VMWare, to test everything before I completely install.

Thanks everyone.

---

### Post by dino99 on 2012-06-08
howto use vmware

[http://www.howtogeek.com/howto/11287/how-to-run-ubuntu-in-windows-7-with-vmware-player/](http://www.howtogeek.com/howto/11287/how-to-run-ubuntu-in-windows-7-with-vmware-player/)

---

### Post by komensky on 2012-07-20
I have the same problem with catalyst 12.6 on fresh amd64 precise w/all updates and kernel 3.4.6 from source.

Did you solve it?  How?

tia

---

### Post by TenPlus1 on 2012-07-21
You can't really test a distribution with all the drivers available if you are inside a virtual setup...  Try installing Ubuntu to a usb flash drive or SD card and booting from that if you're setup allows...  That is how I tested Kubuntu with full driver support and it got to play around with proper driver setup...

---

