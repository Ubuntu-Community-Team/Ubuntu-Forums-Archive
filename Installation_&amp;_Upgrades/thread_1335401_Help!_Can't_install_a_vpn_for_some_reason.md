---
title: "Help! Can't install a vpn for some reason"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by Afsadowski04 on 2009-11-23
I downloaded a VPN client I need for work to the desktop. When I went to install it in the terminal I got:

ricky@ricky-laptop:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.31-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.31-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.31-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/ricky/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/ricky/Desktop/vpnclient/linuxcniapi.o
In file included from /home/ricky/Desktop/vpnclient/Cniapi.h:15,
                 from /home/ricky/Desktop/vpnclient/linuxcniapi.c:31:
/home/ricky/Desktop/vpnclient/GenDefs.h:113: error: conflicting types for ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/home/ricky/Desktop/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/ricky/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
ricky@ricky-laptop:~/Desktop/vpnclient$ 



Any ideas what to do to properly install it?

---

### Post by lemming465 on 2009-11-24
Assuming you are connecting to a Cisco IPSEC VPN appliance, try installing the *vpnc* and *network-manager-vpnc* packages (ubuntu 9.10) instead.

Otherwise ask your network staff for a newer version of the Cisco software; the odds that 3-year old network software will still compile against a brand new Linux kernel are, as you have discovered, zero.  Too many changes in the internal kernel APIs.

---

