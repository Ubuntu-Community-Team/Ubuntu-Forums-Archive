---
title: "installing nvidia card error message"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by helai on 2007-02-22
When i download the driver form nvidia site,and installed on my ubuntu6.1 ,it shows me some messages,and i also don't know whether it is now work well for me

who can tell me how to solve it and just check whether it is ok or not
Thanks in advance

messages listed below


nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu Feb 22 14:44:50 2007

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
-> There appears to already be a driver installed on your system (version: 1.0-
   7184).  As part of installing this driver (version: 1.0-7184), the existing 
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.17-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.17-11-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.17-11-gener
   ic/build SYSOUT=/lib/modules/2.6.17-11-generic/build'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.17-11-generic/build SUBDIRS
   =/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_vers
   ions
   rm -f /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_version
   s/*
   make -f scripts/Makefile.build obj=/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz5923/NVI
   DIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.nv.o
   .d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL_
   _ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O
   2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpre
   ferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestandi
   ng -Iinclude/a
   sm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/
   selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -
   Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -Wno-cast-qual -W
   no-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -
   D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_
   VERSION=0 -DNV_PATCHLEVEL=7184  -DNV_UNIX   -DNV_LINUX   -DNV_INT64_OK   -DN
   VCPU_X86      -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPL
   E_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_PM_MESSAGE_T_PRESEN
   T -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_R
   ANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"
   KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUI
   LD_STR(nvidia)" -c -o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/.tmp_nv.o /tmp/selfgz5923/NVIDIA
   -Linux-x86-1.0-7184-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:47,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:71,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.nv-v
   m.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERN
   EL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector
   -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreestan
   ding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-poin
   ter-sign -I/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv -Wall -
   Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -W
   pointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-compare -
   Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM
   -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSIO
   N=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7184  -DNV_UNIX   -DNV_LINUX   -DNV
   _INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEBUG -DND
   EBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_G
   ET_CLASS_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DN
   V_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_
   PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAM
   E=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfg
   z5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz5923
   /NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:47,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:71,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.os-a
   gp.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KER
   NEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pr
   ototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-protecto
   r -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-float -
   mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffreest
   anding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-po
   inter-sign -I/tmp/selfgz5923/NVIDIA-
   Linux-x86-1.0-7184-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -
   Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -We
   rror -O -fno-common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_
   KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAM
   ES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PAT
   CHLEVEL=7184  -DNV_UNIX   -DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -UDE
   BUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_P
   RESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_
   STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_
   CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" 
   -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)
   " -c -o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_os-ag
   p.o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:47,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:71,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.os-i
   nterface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -
   D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstr
   ict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-pr
   otector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-f
   loat -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -f
   freestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -
   Wno-pointer-sign -I/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE 
   -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR
   _VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7184  -DNV_UNIX   -DNV_LINUX
     -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STR
   UCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -
   DNV_PCI_GET_CLASS_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PR
   ESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_P
   AGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUIL
   D_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" 
   -c -o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_os-inte
   rface.o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-interfa
   ce.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:47,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:71,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.os-r
   egistry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D
   __KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-pro
   tector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-fl
   oat -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ff
   reestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -W
   no-pointer-sign -I/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr
   /src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -
   Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -
   Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -
   DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -
   DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7184  -DNV_UNIX   -
   DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -UDEBUG -U_DEBUG -DNDEBUG -DNV_
   SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_P
   RESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSER
   T_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -D
   NV_VMAP_4_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_S
   TR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz592
   3/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz59
   23/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:47,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/nv-linux.h:71,
                    from /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
     ld -m elf_i386 -m elf_i386  -r -o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-718
   4-pkg1/usr/src/nv/nvidia.o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/us
   r/src/nv/nv-kernel.o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/
   nv/nv.o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nv-vm.o /t
   mp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-agp.o /tmp/selfgz
   5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-interface.o /tmp/selfgz592
   3/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.17-11-generic/scripts/Makefile.modpos
   t
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.17-11-generic/Modu
   le.symvers -I /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/Modu
   les.symvers -o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/Mod
   ules.symvers /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nvidi
   a.o
   WARNING: could not find /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/.nvid
   ia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D_
   _KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-stack-prot
   ector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -msoft-flo
   at -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -mregparm=3 -ffr
   eestanding -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wn
   o-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz5923/NVID
   IA-Linux-x86-1.0-7184-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz5923/NVIDIA-Li
   nux-x86-1.0-7184-pkg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184
   -pkg1/usr/src/nv/nvidia.ko /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/us
   r/src/nv/nvidia.o /tmp/selfgz5923/NVIDIA-Linux-x86-1.0-7184-pkg1/usr/src/nv/
   nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [17179592.016000] EXT3 FS on hdb7, internal journal
   [17179592.016000] EXT3-fs: mounted filesystem with ordered data mode.
   [17179592.060000] NTFS driver 2.1.27 [Flags: R/O MODULE].
   [17179592.116000] NTFS volume version 3.1.
   [17179592.284000] NET: Registered protocol family 17
   [17179598.152000] ACPI: Power Button (FF) [PWRF]
   [17179598.152000] ACPI: Power Button (CM) [PWRB]
   [17179598.288000] ibm_acpi: ec object not found
   [17179598.336000] pcc_acpi: loading...
   [17179598.696000] NET: Registered protocol family 10
   [17179598.696000] lo: Disabled Privacy Extensions
   [17179598.696000] IPv6 over IPv4 tunneling driver
   [17179602.300000] agpgart: Found an AGP 3.0 compliant device at
   0000:00:00.0.
   [17179602.300000] agpgart: Device is in legacy mode, falling back to 2.x
   [17179602.300000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x
   mode
   [17179602.300000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x
   mode
   [17179602.848000] agpgart: Found an AGP 3.0 compliant device at
   0000:00:00.0.
   [17179602.848000] agpgart: Device is in legacy mode, falling back to 2.x
   [17179602.848000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x
   mode
   [17179602.848000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x
   mode
   [17179603.100000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
   [17179603.100000] apm: disabled - APM is not SMP safe.
   [17179608.892000] eth0: no IPv6 routers present
   [17180668.996000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low)
   -> IRQ 177
   [17180668.996000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-7184 
   Tue Aug  1 18:38:58 PDT 2006
WARNING: You appear to be using a modular Xorg release, but nvidia-installer
         was unable to determine the correct X library installation path with
         the `pkg-config` utility.  Please install the Xorg SDK/development
         package for your distribution.
WARNING: nvidia-installer was unable to determine the correct X library
         installation path and will install the NVIDIA X libraries to
         '/usr/lib'.
WARNING: You appear to be using a modular Xorg release, but nvidia-installer
         was unable to determine the correct X module installation path with
         the `pkg-config` utility.  Please install the Xorg SDK/development
         package for your distribution.
WARNING: nvidia-installer was unable to determine the correct X module
         installation path and will install the NVIDIA X driver components to
         '/usr/lib/xorg/modules'.  If X fails to find the NVIDIA X driver
         module, please correct any `pkg-config` problems warned about earlier
         and reinstall the driver.
-> Installing both new and classic TLS OpenGL libraries.
-> Parsing log file:
-> done.
-> Validating previous installation:
-> done.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86 (1.0-7184):
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86 (1.0-7184) is complete.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86' (1.0-7184):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86
   (version: 1.0-7184) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README for details.

---

### Post by renzokuken on 2007-02-22
try using the envy script instead

[www.albertomilone.com](www.albertomilone.com) and look in the projects and guides sections

---

