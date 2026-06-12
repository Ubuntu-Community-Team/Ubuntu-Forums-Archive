---
title: "Nvidia: Can't install (Unable to build kernel module)"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by CheGhe on 2008-06-25
Hi

I'm trying to install Nvidia driver (**NVIDIA-Linux-x86-100.14.11-pkg1.run**) on **Acer Aspire 5520** laptop, GeForce 7000M graphics (Ubuntu 8.04).

After entering **runlevel 3** and running the following:[SIZE="3"][/SIZE]

# sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run

it wants to compile a kernel interface, but at the end returns the error:

**ERROR: Unable to build the NVIDIA kernel module**

Please help as I can't change resolution greater than 800x600.

-----

Content of log file is:

[SIZE="3"][SIZE="2"]nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jun 25 22:25:20 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.24-19-generic/build'
-> Kernel output path: '/lib/modules/2.6.24-19-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvacpi.
   o nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvacpi.o nvidi
   a.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h Modules.symvers
   rm -f -rf .tmp_versions
   rm -f Makefile
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.24-19-gener
   ic/build SYSOUT=/lib/modules/2.6.24-19-generic/build'...
   sh ./conftest.sh "cc" "cc" /lib/modules/2.6.24-19-generic/build /lib/modules
   /2.6.24-19-generic/build cc_sanity_check full_output
   sh ./conftest.sh "cc" "cc" /lib/modules/2.6.24-19-generic/build /lib/modules
   /2.6.24-19-generic/build select_makefile full_output
   make --no-print-directory -f Makefile module
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.24-19-generic/build SUBDIRS
   =/tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz6170/NVIDIA-Linux-x86-100.14.1
   1-pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz6170/NVI
   DIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g 
   -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tm
   p/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv -Wall -Wimplicit -Wr
   eturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith
    -Wno-multichar  -Werror  -O -fno-common -msoft-float          -MD   -Wsign-
   compare
    -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV
   RM -DNV_VERSION_STRING=\"100.14.11\" -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_S
   TRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -
   DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_S
   TATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_OLD_MM_KGDB_BREAKPOINT_PRESENT
   -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_ACQUIRE_CONS
   OLE_SEM_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD
   _BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz6
   170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:49,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/sr
   c/nv/nv-linux.h:78,
                    from /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
   /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.c: In function
   ‘nvidia_init_module’:
   /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.c:1326: error:
   too many arguments to function ‘kmem_cache_create’
   /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.c:1435: error:
   too many arguments to function ‘kmem_cache_create’
   /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.c:1569: error:
   void value not ignored as it ought to be
   /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.c: In function
   ‘nvidia_exit_module’:
   /tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.c:1601: error:
   void value not ignored as it ought to be
   make[3]: *** [/tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz6170/NVIDIA-Linux-x86-100.14.11-pkg1/usr/sr
   c/nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).[/SIZE][/SIZE]

---

### Post by sdennie on 2008-06-25
Is there a reason you want to use a driver that old?  That's very out of date and it may not work with 2.6.24.  Also, are you sure you have the kernel headers installed?  Try:

```

sudo apt-get install linux-headers-generic

```

---

### Post by CheGhe on 2008-06-26
> **vor said:**
> Is there a reason you want to use a driver that old?  That's very out of date and it may not work with 2.6.24.  Also, are you sure you have the kernel headers installed?  Try:

```

sudo apt-get install linux-headers-generic

```

I have headers installed. I tried also with version NVIDIA-Linux-x86-1.0-8762-pkg1.run, and it's the same.

---

### Post by Neo0351 on 2008-06-26
try this
[http://ubuntuforums.org/showpost.php?p=4558708&postcount=37](http://ubuntuforums.org/showpost.php?p=4558708&postcount=37)

---

