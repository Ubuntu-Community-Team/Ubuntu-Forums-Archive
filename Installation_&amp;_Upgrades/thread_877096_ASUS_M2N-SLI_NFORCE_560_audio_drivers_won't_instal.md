---
title: "ASUS M2N-SLI NFORCE 560 audio drivers won't install"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by thedude1373 on 2008-08-01
Hi, I'm new to these forums and relatively new to Ubuntu. I've been trying for the past few days to install the audio drivers for my motherboards onboard sound. when i run the command ```
sudo sh NFORCE-Linux-x86-1[1].0-0311-pkg1.run
``` it tells me > No precompiled kernel interface was found to match your kernel; this means that the installer will need to compile a new kernel interface. I hit ok and after it takes a second to do something it comes back with > ERROR: The NVIDIA kernel module was not created.
 Here is the output of '/var/log/nvidia-nforce-installer.log' > nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Fri Aug  1 12:16:11 2008

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-8)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.24-19-generic (buildd@terranova) (gcc
   version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.24-19-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-19-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.24-19-generic/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.24-19-gen
   eric/build SYSOUT=/lib/modules/2.6.24-19-generic/build'...
   make -C /lib/modules/2.6.24-19-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.24-19-generic \
   	KBUILD_EXTMOD="/tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main"
   -f /usr/src/linux-headers-2.6.24-19-generic/Makefile \
   	modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.tmp_ve
   rsions ; rm -f /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.
   tmp_versions/*
   make -f /usr/src/linux-headers-2.6.24-19-generic/scripts/Makefile.build obj=
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main
     cc -Wp,-MD,/tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.nv
   alinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D_
   _KERNEL__ -I/usr/src/linux-headers-lum- -I/usr/src/linux-headers-lbm- -Iincl
   ude -Iinclude2 -I/usr/src/linux-headers-2.6.24-19-generic/include -include i
   nclude/linux/autoconf.h  -I/tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nv
   sound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-alia
   sing -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-floa
   t -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -
   mtune=generic -ffreestanding -maccumulate-outgoing-args -I/usr/src/linux-hea
   ders-2.6.24-19-generic/include/asm-x86/mach-default -Iinclude/asm-x86/mach-d
   efault -fomit-frame-pointer -g -fno-stack-protector -Wdeclaration-after-stat
   ement -Wno-pointer-sign  -I/tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nv
   sound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual
   -Wno-error -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KB
   UILD_BASENAME=KBUILD_
   STR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /tmp/selfgz9337
   /NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/.tmp_nvalinux.o /tmp/selfgz9337
   /NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:9,
                    from /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:19:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:29:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main/nvalinux.c:49:
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.h: At t
   op level:
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.h:46: e
   rror: conflicting types for ‘uintptr_t’
   include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was
   here
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c: In f
   unction ‘AosFpuSave’:
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:181: 
   error: ‘struct task_struct’ has no member named ‘thread_info’
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:191: 
   error: ‘struct task_struct’ has no member named ‘thread_info’
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:214: 
   error: ‘struct task_struct’ has no member named ‘thread_info’
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c: In f
   unction ‘AosFpuRestore’:
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:234: 
   error: ‘struct task_struct’ has no member named ‘thread_info’
   /tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nvalinux.c:235: 
   error: ‘struct task_struct’ has no member named ‘thread_info’
   make[4]: *** [/tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound/main/nv
   alinux.o] Error 1
   make[3]: *** [_module_/tmp/selfgz9337/NFORCE-Linux-x86-1.0-0311-pkg1/nvsound
   /main] Error 2
   make[2]: *** [sub-make] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
Any help is greatly appreciated

---

