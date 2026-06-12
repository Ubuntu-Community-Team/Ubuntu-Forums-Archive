---
title: "VMware Player on Lucid fails"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by everyday847 on 2010-02-23
While on Karmic, I'd had a Windows VM for a couple of games that would run poorly under Wine. Upon trying to open it after installing Lucid, I get a message reading "Before you can run VMware, several modules must be compiled and loaded into the running kernel." When I click Install (which is actually _Install), it succeeds in "Stopping VMware Services" and "Virtual Machine Monitor," fails at "Virtual Network Device" and succeeds at "VMware Blocking Filesystem," "Virtual Machine Communication Interface" and "VMCI Sockets." On the basis of the Virtual Network Device failure, it fails to start.

It gives me the error message "Unable to start services. See log file /tmp/vmware-root/setup-14385.log for details."

The contents of that file, with the failed module bolded, are
```
Feb 23 16:10:56.844: app-3078969024| Log for VMware Workstation pid=14385 version=7.0.0 build=build-203739 option=Release
Feb 23 16:10:56.844: app-3078969024| The process is 32-bit.
Feb 23 16:10:56.844: app-3078969024| Host codepage=UTF-8 encoding=UTF-8
Feb 23 16:10:56.844: app-3078969024| Logging to /tmp/vmware-root/setup-14385.log
Feb 23 16:10:57.029: app-3078969024| modconf query interface initialized
Feb 23 16:10:57.030: app-3078969024| modconf library initialized
Feb 23 16:10:57.065: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.071: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.080: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.094: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.105: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.163: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.168: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.172: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.176: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.180: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.198: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.203: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.207: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.211: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.215: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.219: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.229: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.266: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.270: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.274: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.278: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.282: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.287: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.296: app-3078969024| Your GCC version: 4.4
Feb 23 16:10:57.343: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.347: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.351: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.355: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.359: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.635: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:10:57.635: app-3078969024| Building module vmmon.
Feb 23 16:10:57.636: app-3078969024| Extracting the sources of the vmmon module.
Feb 23 16:10:57.649: app-3078969024| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Feb 23 16:11:03.768: app-3078969024| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Feb 23 16:11:03.769: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vmmon.o
Feb 23 16:11:04.429: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vmmon.ko
Feb 23 16:11:05.450: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
[B]Feb 23 16:11:05.451: app-3078969024| Building module vmnet.
Feb 23 16:11:05.451: app-3078969024| Extracting the sources of the vmnet module.
Feb 23 16:11:05.463: app-3078969024| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Feb 23 16:11:11.730: app-3078969024| Failed to compile module vmnet![/B]
Feb 23 16:11:11.737: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:11:11.737: app-3078969024| Building module vmblock.
Feb 23 16:11:11.737: app-3078969024| Extracting the sources of the vmblock module.
Feb 23 16:11:11.749: app-3078969024| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Feb 23 16:11:16.269: app-3078969024| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Feb 23 16:11:16.270: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vmblock.o
Feb 23 16:11:16.906: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vmblock.ko
Feb 23 16:11:17.915: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:11:17.915: app-3078969024| Building module vmci.
Feb 23 16:11:17.915: app-3078969024| Extracting the sources of the vmci module.
Feb 23 16:11:17.927: app-3078969024| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Feb 23 16:11:24.351: app-3078969024| Installing module vmci from /tmp/vmware-root/modules/vmci.o.
Feb 23 16:11:24.351: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vmci.o
Feb 23 16:11:25.078: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vmci.ko
Feb 23 16:11:26.066: app-3078969024| Trying to find a suitable PBM set for kernel 2.6.32-14-generic.
Feb 23 16:11:26.067: app-3078969024| Building module vmci.
Feb 23 16:11:26.067: app-3078969024| Extracting the sources of the vmci module.
Feb 23 16:11:26.081: app-3078969024| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Feb 23 16:11:26.882: app-3078969024| Building module vsock.
Feb 23 16:11:26.882: app-3078969024| Extracting the sources of the vsock module.
Feb 23 16:11:26.899: app-3078969024| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vsock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-14-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Feb 23 16:11:31.455: app-3078969024| Installing module vsock from /tmp/vmware-root/modules/vsock.o.
Feb 23 16:11:31.456: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vsock.o
Feb 23 16:11:32.095: app-3078969024| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-14-generic/misc/vsock.ko
```

Any thoughts?

---

### Post by Ibidem on 2010-02-23
Is the kernel compiled with GCC 4.4, or is it 4.2? Modules only work right if they are compiled with the same GCC as the kernel, and I seem to recall hearing that the kernel is still built with 4.2.

---

### Post by everyday847 on 2010-02-23
Look at that, a solution (for me, at least): [this patch]("http://communities.vmware.com/message/1401588#1401588") is all you need.

---

### Post by everyday847 on 2010-02-23
> **Ibidem said:**
> Is the kernel compiled with GCC 4.4, or is it 4.2? Modules only work right if they are compiled with the same GCC as the kernel, and I seem to recall hearing that the kernel is still built with 4.2.
No idea; I do know that my version of GCC was updated in a recent round of updates. I'm surprised that that would make modules ornery; perhaps the kernel was subsequently recompiled with 4.4.

---

### Post by marcog42 on 2010-02-26
I was having the same problem after upgrading to Alpha 3.  I was trying to install VMware Workstation 7.0.0 and unable to get the modules installed. I tried the patch indicated in this thread, but it didn't work. I uninstalled 7.0.0 and installed 7.0.1 and, as if by magic, it worked.  It didn't even ask to install the modules.  It's working with no problems now. YMMV

---

