---
title: "Anyone running VMWare Player on Lucid Lynx host?"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by taylorkh on 2010-03-22
I have tried to install VMWare Player 3.0 64 bit on beta 1 64 bit.  It fails to build the network and communications modules as shown in the log excerpts:> Mar 22 12:17:15.636: app-140551780415232| Building module vmnet.
Mar 22 12:17:15.636: app-140551780415232| Extracting the sources of the vmnet module.
Mar 22 12:17:15.646: app-140551780415232| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only autMar 22 12:17:15.636: app-140551780415232| Building module vmnet.
Mar 22 12:17:15.636: app-140551780415232| Extracting the sources of the vmnet module.
Mar 22 12:17:15.646: app-140551780415232| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 22 12:17:16.335: app-140551780415232| Failed to compile module vmnet!

Mar 22 12:17:18.181: app-140551780415232| Building module vmci.
Mar 22 12:17:18.181: app-140551780415232| Extracting the sources of the vmci module.
Mar 22 12:17:18.191: app-140551780415232| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 22 12:17:18.745: app-140551780415232| Failed to compile module vmci!
o-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 22 12:17:16.335: app-140551780415232| Failed to compile module vmnet!
 

Any suggestions?

TIA,

Ken

---

### Post by phjr on 2010-03-23
I have the same problem :-(   
EDIT: I just found this in another thread and it works: [http://communities.vmware.com/message/1401588#1401588](http://communities.vmware.com/message/1401588#1401588)

---

### Post by boot_sectorz on 2010-03-23
Same problem here :( this is a part of the log that I think is relevant

```

Mar 23 10:44:52.245: app-140247155754752| Building module vmmon.
Mar 23 10:44:52.267: app-140247155754752| Extracting the sources of the vmmon module.
Mar 23 10:44:52.329: app-140247155754752| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 23 10:45:02.400: app-140247155754752| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Mar 23 10:45:02.401: app-140247155754752| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-16-generic/misc/vmmon.o
Mar 23 10:45:05.001: app-140247155754752| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-16-generic/misc/vmmon.ko
Mar 23 10:45:18.214: app-140247155754752| Trying to find a suitable PBM set for kernel 2.6.32-16-generic.
Mar 23 10:45:18.215: app-140247155754752| Building module vmnet.
Mar 23 10:45:18.215: app-140247155754752| Extracting the sources of the vmnet module.
Mar 23 10:45:18.270: app-140247155754752| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 23 10:45:24.777: app-140247155754752| Failed to compile module vmnet!
Mar 23 10:45:24.782: app-140247155754752| Trying to find a suitable PBM set for kernel 2.6.32-16-generic.
Mar 23 10:45:24.783: app-140247155754752| Building module vmblock.
Mar 23 10:45:24.783: app-140247155754752| Extracting the sources of the vmblock module.
Mar 23 10:45:24.883: app-140247155754752| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 23 10:45:29.210: app-140247155754752| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Mar 23 10:45:29.211: app-140247155754752| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-16-generic/misc/vmblock.o
Mar 23 10:45:29.796: app-140247155754752| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-16-generic/misc/vmblock.ko
Mar 23 10:45:30.917: app-140247155754752| Trying to find a suitable PBM set for kernel 2.6.32-16-generic.
Mar 23 10:45:30.917: app-140247155754752| Building module vmci.
Mar 23 10:45:30.917: app-140247155754752| Extracting the sources of the vmci module.
Mar 23 10:45:30.959: app-140247155754752| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 23 10:45:32.308: app-140247155754752| Failed to compile module vmci!
Mar 23 10:45:32.313: app-140247155754752| Trying to find a suitable PBM set for kernel 2.6.32-16-generic.
Mar 23 10:45:32.314: app-140247155754752| Building module vmci.
Mar 23 10:45:32.314: app-140247155754752| Extracting the sources of the vmci module.
Mar 23 10:45:32.326: app-140247155754752| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-16-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Mar 23 10:45:33.288: app-140247155754752| Failed to compile module vmci!

```

---

### Post by boot_sectorz on 2010-03-23
Sorry double post... Check all above

---

### Post by taylorkh on 2010-03-23
Thanks phjr.  I will have to give the patch a try and see if it works for Player.

Ken

---

### Post by taylorkh on 2010-03-23
Good news! 

The patch on the VMWare forum fixes Player 3.0

Better news!!

Version 3.0.1 - 227600 - 02/18/10 works on Lucid beta 1 without the need to apply the patch.

Ken

---

