---
title: "Very anoying upgrade, deleted the one APP [VMWARE] I use most."
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ChrisStockton on 2008-04-25
My upgrade removed VMWAREServer, from system tools etc. What sucks more is the package is deleted. Now when I try to re-install from the source files on the vmware server site I get compile errors.



Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config3/vmmon-only/common/cpuid.o
In file included from include/asm/bitops.h:2,
                 from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:74,
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config3/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config3/vmmon-only/common/cpuid.c:15:
include/asm/bitops_32.h:9:2: error: #error only <linux/bitops.h> can be included directly
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/cpuid.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.



I tried the advice for some any-any patch and it did not work. Not sure what to do now. I need to login to my vms for work.

Anyone got any ideas?

-Chris

---

