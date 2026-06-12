---
title: "Problems with module-assistant when trying to install shfs"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by richie on 2005-05-02
Hi

I've been trying to find the solution to this problem online for a few days now and I haven't managed to find out what I'm doing wrong.Basically I'm trying to install shfs .I've downloaded the package source code ,shfs-source shfs-utils. However when I try to build the kernel module I keep getting the response "Bad luck, the kernel headers for this kernel version could not be found and you did not specify other kernel headers to use." . It then tells me to try to run module-assistant prepare which I do but to no avail. Would anybody out there know what I'm doing wrong? I'd imagine is something fairly simple

Thanks

---

### Post by richie on 2005-05-02
P.s I did mange to get the build started by using the -k argument with module-assistant but it still didn't make up fully.

The logfile said ...


make -C Linux-2.6 KERNEL_SOURCES=/usr/src/linux-headers-2.6.10-5-386/ MODVERSIONS=detect KERNEL=linux-2.6.10
make[1]: Entering directory `/usr/src/modules/shfs/Linux-2.6'
make -C /usr/src/linux-headers-2.6.10-5-386/ SUBDIRS=/usr/src/modules/shfs/Linux-2.6 modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.10-5-386'
  CC [M]  /usr/src/modules/shfs/Linux-2.6/dcache.o
In file included from include/asm/system.h:5,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from /usr/src/modules/shfs/Linux-2.6/dcache.c:16:
include/linux/kernel.h:10:20: stdarg.h: No such file or directory
In file included from include/asm/system.h:5,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from /usr/src/modules/shfs/Linux-2.6/dcache.c:16:
include/linux/kernel.h:82: error: syntax error before "va_list"
include/linux/kernel.h:82: warning: function declaration isn't a prototype
include/linux/kernel.h:85: error: syntax error before "va_list"
include/linux/kernel.h:85: warning: function declaration isn't a prototype
include/linux/kernel.h:88: error: syntax error before "va_list"
include/linux/kernel.h:88: warning: function declaration isn't a prototype
include/linux/kernel.h:92: error: syntax error before "va_list"
include/linux/kernel.h:92: warning: function declaration isn't a prototype
include/linux/kernel.h:102: error: syntax error before "va_list"
include/linux/kernel.h:102: warning: function declaration isn't a prototype
make[3]: *** [/usr/src/modules/shfs/Linux-2.6/dcache.o] Error 1
make[2]: *** [_module_/usr/src/modules/shfs/Linux-2.6] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.10-5-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'
make: *** [binary-modules] Error 2




It can't seem to find stdarg.h , but I think it's there ok

---

