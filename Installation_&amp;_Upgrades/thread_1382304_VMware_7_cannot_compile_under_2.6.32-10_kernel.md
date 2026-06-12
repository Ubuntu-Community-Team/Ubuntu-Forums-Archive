---
title: "VMware 7 cannot compile under 2.6.32-10 kernel"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by glenik on 2010-01-15
I upgraded to Ubuntu 10.04 2.6.32-10-generic today. After a succesful update that fixed a couple of nagging problems on my laptop (nice work guys) I started VMware Workstation. I got the expected "Before you can run VMware, several modules must be compiled..."

The compile errors out and points to the setup log.  I have searched and found several very similar posts all relating to build-essential or kernel-headers not being installed. I have verified both are installed and up to date.  Any suggestions?

Here's the important part of the log:

```

Jan 15 17:39:16.079: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:16.080: app-139708855981824| Building module vmmon.
Jan 15 17:39:16.093: app-139708855981824| Extracting the sources of the vmmon module.
Jan 15 17:39:16.183: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:23.446: app-139708855981824| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Jan 15 17:39:23.447: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmmon.o
Jan 15 17:39:25.463: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmmon.ko
Jan 15 17:39:34.929: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:34.929: app-139708855981824| Building module vmnet.
Jan 15 17:39:34.929: app-139708855981824| Extracting the sources of the vmnet module.
Jan 15 17:39:34.978: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:39.705: app-139708855981824| Failed to compile module vmnet!
Jan 15 17:39:39.708: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:39.708: app-139708855981824| Building module vmblock.
Jan 15 17:39:39.708: app-139708855981824| Extracting the sources of the vmblock module.
Jan 15 17:39:39.761: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:42.590: app-139708855981824| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Jan 15 17:39:42.591: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmblock.o
Jan 15 17:39:43.103: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmblock.ko
Jan 15 17:39:43.962: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:43.963: app-139708855981824| Building module vmci.
Jan 15 17:39:43.963: app-139708855981824| Extracting the sources of the vmci module.
Jan 15 17:39:44.011: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:44.942: app-139708855981824| Failed to compile module vmci!
Jan 15 17:39:44.947: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:44.948: app-139708855981824| Building module vmci.
Jan 15 17:39:44.948: app-139708855981824| Extracting the sources of the vmci module.
Jan 15 17:39:44.955: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:46.227: app-139708855981824| Failed to compile module vmci!
Jan 15 17:39:51.109: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.114: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.115: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.117: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.119: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.122: app-139708855981824| Your GCC version: 4.4
Jan 15 17:39:51.127: app-139708855981824| Your GCC version: 4.4
Jan 15 17:39:51.155: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.156: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.158: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.159: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.161: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.333: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:51.334: app-139708855981824| Building module vmmon.
Jan 15 17:39:51.334: app-139708855981824| Extracting the sources of the vmmon module.
Jan 15 17:39:51.344: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:52.179: app-139708855981824| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Jan 15 17:39:52.180: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmmon.o
Jan 15 17:39:52.716: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmmon.ko
Jan 15 17:39:53.516: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:53.516: app-139708855981824| Building module vmnet.
Jan 15 17:39:53.516: app-139708855981824| Extracting the sources of the vmnet module.
Jan 15 17:39:53.524: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:54.354: app-139708855981824| Failed to compile module vmnet!
Jan 15 17:39:54.357: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:54.357: app-139708855981824| Building module vmblock.
Jan 15 17:39:54.357: app-139708855981824| Extracting the sources of the vmblock module.
Jan 15 17:39:54.366: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:55.263: app-139708855981824| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Jan 15 17:39:55.264: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmblock.o
Jan 15 17:39:55.772: app-139708855981824| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-10-generic/misc/vmblock.ko
Jan 15 17:39:56.575: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:56.575: app-139708855981824| Building module vmci.
Jan 15 17:39:56.575: app-139708855981824| Extracting the sources of the vmci module.
Jan 15 17:39:56.583: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:56.997: app-139708855981824| Failed to compile module vmci!
Jan 15 17:39:57.001: app-139708855981824| Trying to find a suitable PBM set for kernel 2.6.32-10-generic.
Jan 15 17:39:57.002: app-139708855981824| Building module vmci.
Jan 15 17:39:57.002: app-139708855981824| Extracting the sources of the vmci module.
Jan 15 17:39:57.010: app-139708855981824| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-10-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Jan 15 17:39:57.417: app-139708855981824| Failed to compile module vmci!
 
```J

---

### Post by glenik on 2010-01-15
Really? Popular app and a new distro of Ubuntu and nobody has anything for compile problems?

---

### Post by Vignesh S on 2010-01-16
I have the same problem in the 2.6.32 kernel too. I have no idea what's going on :-(

---

### Post by eris23 on 2010-01-18
[http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32](http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32)

---

### Post by eris23 on 2010-01-18
[http://communities.vmware.com/message/1401588#1401588](http://communities.vmware.com/message/1401588#1401588)

---

