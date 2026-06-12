---
title: "Failed to build busybox under Ubuntu 12.04"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2013-01-06
Hi, all:

I downloaded two versions of busybox
a) the formal release BusyBox 1.20.2
b) current git version git clone git://busybox.net/busybox.git
Whenever I build busybox (not matter which version it is), I got the following error messages:


> /usr/include/linux/sysinfo.h:8:2: error: unknown type name '__kernel_long_t'
/usr/include/linux/sysinfo.h:9:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:10:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:11:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:12:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:13:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:14:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:15:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:18:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:19:2: error: unknown type name '__kernel_ulong_t'
/usr/include/linux/sysinfo.h:21:22: error: '__kernel_ulong_t' undeclared here (not in a function)
make[1]: *** [init/init.o] Error 1
make: *** [init] Error 2


The above error messages are weird IMO.

I simply traced down the files:

> buxybox/init/init.c # include <sys/sysinfo.h>
/usr/include/i386-linux-gnu/sys/sysinfo.h #include <linux/kernel.h>
/usr/include/linux/kernel.h #include <linux/sysinfo.h>
/usr/include/linux/sysinfo.h #include <linux/types.h>
/usr/include/linux/types.h #include <linux/posix_types.h>
/usr/include/linux/posix_types.h #include <asm/posix_types.h>
/usr/include/asm/posix_types.h #include <asm/posix_types_32.h>
/usr/include/asm-generic/posix_types_32.h #include <asm-generic/posix_types.h>
/usr/include/asm-generic/posix_types.h

#ifndef __kernel_long_t
typedef long		__kernel_long_t;
typedef unsigned long	__kernel_ulong_t;
#endif



I can't believe that '__kernel_long_t' and '__kernel_ulong_t' haven't been found.
Can anybody help please?


Pei

---

