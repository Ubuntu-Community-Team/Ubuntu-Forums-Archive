---
title: "VMware workstation 7 untable to compile with new kernel."
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by devroute on 2010-08-20
Okay i installed linux kernel 2.6.35.2 and now vmware wont run been searching for a few hours for a "fix" found a few files but they don't seem to work here's log from vmware updater any help greatly appreciated

```

Aug 20 01:04:09.520: app-140689147180800| Log for VMware Workstation pid=22622 version=7.1.1 build=build-282343 option=Release
Aug 20 01:04:09.520: app-140689147180800| The process is 64-bit.
Aug 20 01:04:09.520: app-140689147180800| Host codepage=UTF-8 encoding=UTF-8
Aug 20 01:04:09.520: app-140689147180800| Logging to /tmp/vmware-root/setup-22622.log
Aug 20 01:04:09.607: app-140689147180800| modconf query interface initialized
Aug 20 01:04:09.607: app-140689147180800| modconf library initialized
Aug 20 01:04:09.624: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.627: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.632: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.639: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.644: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.660: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.662: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.664: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.665: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.667: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.675: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.677: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.678: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.680: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.682: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.684: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.689: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.706: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.708: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.709: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.711: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.712: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.715: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.720: app-140689147180800| Your GCC version: 4.4
Aug 20 01:04:09.742: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.744: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.746: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.747: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:09.749: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:10.018: app-140689147180800| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:04:10.018: app-140689147180800| Building module vmmon.
Aug 20 01:04:10.018: app-140689147180800| Extracting the sources of the vmmon module.
Aug 20 01:04:10.025: app-140689147180800| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Aug 20 01:04:12.037: app-140689147180800| Failed to compile module vmmon!

```

---

### Post by devroute on 2010-08-20
well after a bit of messing around now i get

```

Aug 20 01:55:04.389: app-140622668777216| Log for VMware Workstation pid=14281 version=7.1.1 build=build-282343 option=Release
Aug 20 01:55:04.389: app-140622668777216| The process is 64-bit.
Aug 20 01:55:04.389: app-140622668777216| Host codepage=UTF-8 encoding=UTF-8
Aug 20 01:55:04.389: app-140622668777216| Logging to /tmp/vmware-root/setup-14281.log
Aug 20 01:55:04.477: app-140622668777216| modconf query interface initialized
Aug 20 01:55:04.478: app-140622668777216| modconf library initialized
Aug 20 01:55:04.494: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.497: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.503: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.510: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.515: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.532: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.533: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.535: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.536: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.538: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.547: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.549: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.551: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.552: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.554: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.556: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.561: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.579: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.582: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.584: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.585: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.587: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.589: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.594: app-140622668777216| Your GCC version: 4.4
Aug 20 01:55:04.618: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.619: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.621: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.622: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.624: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.905: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:04.905: app-140622668777216| Building module vmmon.
Aug 20 01:55:04.905: app-140622668777216| Extracting the sources of the vmmon module.
Aug 20 01:55:04.912: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Aug 20 01:55:08.857: app-140622668777216| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Aug 20 01:55:08.859: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmmon.o
Aug 20 01:55:09.382: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmmon.ko
Aug 20 01:55:10.125: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:10.125: app-140622668777216| Building module vmnet.
Aug 20 01:55:10.125: app-140622668777216| Extracting the sources of the vmnet module.
Aug 20 01:55:10.131: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Aug 20 01:55:15.203: app-140622668777216| Installing module vmnet from /tmp/vmware-root/modules/vmnet.o.
Aug 20 01:55:15.205: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmnet.o
Aug 20 01:55:15.628: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmnet.ko
Aug 20 01:55:16.358: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:16.358: app-140622668777216| Building module vmblock.
Aug 20 01:55:16.358: app-140622668777216| Extracting the sources of the vmblock module.
Aug 20 01:55:16.364: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Aug 20 01:55:19.406: app-140622668777216| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Aug 20 01:55:19.407: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmblock.o
Aug 20 01:55:19.823: app-140622668777216| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.35.2-custom/misc/vmblock.ko
Aug 20 01:55:20.546: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:20.547: app-140622668777216| Building module vmci.
Aug 20 01:55:20.547: app-140622668777216| Extracting the sources of the vmci module.
Aug 20 01:55:20.552: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Aug 20 01:55:21.505: app-140622668777216| Failed to compile module vmci!
Aug 20 01:55:21.508: app-140622668777216| Trying to find a suitable PBM set for kernel 2.6.35.2-custom.
Aug 20 01:55:21.508: app-140622668777216| Building module vmci.
Aug 20 01:55:21.508: app-140622668777216| Extracting the sources of the vmci module.
Aug 20 01:55:21.515: app-140622668777216| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35.2-custom/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Aug 20 01:55:21.916: app-140622668777216| Failed to compile module vmci!

```

---

