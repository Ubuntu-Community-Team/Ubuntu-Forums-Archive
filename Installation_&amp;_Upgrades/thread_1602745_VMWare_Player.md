---
title: "VMWare Player"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by pi091997 on 2010-10-21
Hi All!

I just updated to 10.10, and I am having issues with vm.  It starts to load, then says that I must compile some modules.  However, it doesn't work...

The Log File:
Oct 21 19:30:57.926: app-140240583857920| Log for VMware Workstation pid=6067 version=7.1.2 build=build-301548 option=Release
Oct 21 19:30:57.926: app-140240583857920| The process is 64-bit.
Oct 21 19:30:57.926: app-140240583857920| Host codepage=UTF-8 encoding=UTF-8
Oct 21 19:30:57.926: app-140240583857920| Logging to /tmp/vmware-root/setup-6067.log
Oct 21 19:30:58.063: app-140240583857920| modconf query interface initialized
Oct 21 19:30:58.064: app-140240583857920| modconf library initialized
Oct 21 19:30:58.104: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.112: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.126: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.148: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.163: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.207: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.212: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.215: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.218: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.221: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.244: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.247: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.250: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.252: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.255: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.262: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.276: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.319: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.321: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.324: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.327: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.329: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.336: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.347: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.406: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.410: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.413: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.416: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.418: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.614: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.615: app-140240583857920| Building module vmmon.
Oct 21 19:30:58.615: app-140240583857920| Extracting the sources of the vmmon module.
Oct 21 19:30:58.631: app-140240583857920| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Oct 21 19:31:02.123: app-140240583857920| Failed to compile module vmmon!
Oct 21 19:31:04.853: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.858: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.861: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.864: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.867: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.874: app-140240583857920| Your GCC version: 4.4
Oct 21 19:31:04.887: app-140240583857920| Your GCC version: 4.4
Oct 21 19:31:04.961: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.967: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.970: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.973: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.976: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:05.191: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:05.191: app-140240583857920| Building module vmmon.
Oct 21 19:31:05.191: app-140240583857920| Extracting the sources of the vmmon module.
Oct 21 19:31:05.213: app-140240583857920| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Oct 21 19:31:06.957: app-140240583857920| Failed to compile module vmmon!

Idk what to do!!!

plz help!

:D

---

### Post by csmth on 2010-10-23
> **pi091997 said:**
> Hi All!

I just updated to 10.10, and I am having issues with vm.  It starts to load, then says that I must compile some modules.  However, it doesn't work...

The Log File:
Oct 21 19:30:57.926: app-140240583857920| Log for VMware Workstation pid=6067 version=7.1.2 build=build-301548 option=Release
Oct 21 19:30:57.926: app-140240583857920| The process is 64-bit.
Oct 21 19:30:57.926: app-140240583857920| Host codepage=UTF-8 encoding=UTF-8
Oct 21 19:30:57.926: app-140240583857920| Logging to /tmp/vmware-root/setup-6067.log
Oct 21 19:30:58.063: app-140240583857920| modconf query interface initialized
Oct 21 19:30:58.064: app-140240583857920| modconf library initialized
Oct 21 19:30:58.104: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.112: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.126: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.148: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.163: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.207: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.212: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.215: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.218: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.221: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.244: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.247: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.250: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.252: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.255: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.262: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.276: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.319: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.321: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.324: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.327: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.329: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.336: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.347: app-140240583857920| Your GCC version: 4.4
Oct 21 19:30:58.406: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.410: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.413: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.416: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.418: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.614: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:30:58.615: app-140240583857920| Building module vmmon.
Oct 21 19:30:58.615: app-140240583857920| Extracting the sources of the vmmon module.
Oct 21 19:30:58.631: app-140240583857920| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Oct 21 19:31:02.123: app-140240583857920| Failed to compile module vmmon!
Oct 21 19:31:04.853: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.858: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.861: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.864: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.867: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.874: app-140240583857920| Your GCC version: 4.4
Oct 21 19:31:04.887: app-140240583857920| Your GCC version: 4.4
Oct 21 19:31:04.961: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.967: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.970: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.973: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:04.976: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:05.191: app-140240583857920| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Oct 21 19:31:05.191: app-140240583857920| Building module vmmon.
Oct 21 19:31:05.191: app-140240583857920| Extracting the sources of the vmmon module.
Oct 21 19:31:05.213: app-140240583857920| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Oct 21 19:31:06.957: app-140240583857920| Failed to compile module vmmon!

Idk what to do!!!

plz help!

:D
I got the same problem on VMware Player 3.0.1. The solution at the following link works: [https://answers.launchpad.net/vmware-ubuntu/+question/128677](https://answers.launchpad.net/vmware-ubuntu/+question/128677)

---

### Post by Mason A. Cobb on 2010-11-30
That's a great link, however, the original question was referring to the FREE version of VMware PLAYER, NOT vmware workstation, which is a paid product. 

I too have had this problem installing the player in ubuntu studio 10.10

This patch script doesn't specifically fix the problem, however, it did allow the vmware installer to do what it needed to do to finish the installation(VMware Player 3.1.3)

Thanks. Great Post, needed to clarify that fact though since all the links in the post go to threads refering to the Workstation install, NOt the player install

---

