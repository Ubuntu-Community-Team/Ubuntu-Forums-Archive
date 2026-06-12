---
title: "VMWare won't compile after upgrade to 10.04"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by ubnewbie2 on 2010-05-28
Just upgraded to 10.04 and tried to start VMWare player.  It tried to recompile it's modules but failed on one of them.  Log copied below...

```
May 29 12:07:07.110: app| Log for VMware Workstation pid=3105 version=6.5.2 build=build-156735 option=Release
May 29 12:07:07.118: app| Host codepage=UTF-8 encoding=UTF-8
May 29 12:07:07.118: app| Logging to /tmp/vmware-root/setup-3105.log
May 29 12:07:08.703: app| Extracting the sources of the vmmon module.
May 29 12:07:08.881: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
May 29 12:07:17.850: app| Extracting the sources of the vmmon module.
May 29 12:07:17.983: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
```

---

