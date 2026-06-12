---
title: "VMware server PTE_PFN_MASK error"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by merville on 2008-10-31
Hi all,

Just upgraded to 8.10 from 8.04 and everything is working fine apart from VMware server.  Whenever a new kernel is installed, VMware requires a rebuild of the modules:

```

vmware [enter]
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

Everything progresses fine until module compilation time:

```


None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.27-7-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.27-7-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:49:
/tmp/vmware-config3/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from include/asm/pda.h:8,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:12:
include/asm/page.h:22:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config3/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:71:
/tmp/vmware-config3/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config3/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config3/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config3/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.


```

Any suggestions ? 

Many thanks in advance .....

---

