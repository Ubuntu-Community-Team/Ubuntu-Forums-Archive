---
title: "Trying to Install Nvidia Driver - Kernel prob..."
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by Stallone on 2005-08-06
Hello.

So I have been trying to install my Nvidia Drivers, but there is always a problem with my kernel... It try's to compile it, but says something about my kernel source and about a file called 'nvidia.ko'. Here's the log that it made:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Aug  6 20:35:10 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Kernel source path: '/lib/modules/2.6.10-5-386/build'
-> Performing CC test with CC="cc".
-> Performing rivafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv.o nv-vm.o os-
   agp.o os-interface.o os-registry.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.10-5-386/bu
   ild SYSOUT=/lib/modules/2.6.10-5-386/build'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.10-5-386/build SUBDIRS=/tmp
   /selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv modules
   mkdir -p /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_vers
   ions
   make -f scripts/Makefile.build obj=/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667
   -pkg1/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz9696/NVI
   DIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.nv.o
   .d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-frame
   -pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Iincl
   ude/asm-i386/mach-default  -I/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/
   usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD 
    -Wsign-compare -Wno-c
   ast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_G
   NU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 
   -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SI
   GNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT 
   -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESE
   NT  -DMODULE -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz9
   696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz9696/NVID
   IA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.nv-v
   m.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-fr
   ame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -Ii
   nclude/asm-i386/mach-default  -I/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pk
   g1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscr
   ipts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -
   O -fno-common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL
   _NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D_
   _KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVE
   L=7667  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RAN
   GE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DN
   V_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=nv_v
   m -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pk
   g1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/us
   r/src/nv/nv-vm.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-vm.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.os-a
   gp.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fomit-f
   rame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i386 -I
   include/asm-i386/mach-default  -I/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-p
   kg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subsc
   ripts
    -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD  
   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ 
   -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  
   -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667  -UDEBUG -U_D
   EBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHAN
   GE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRES
   ENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_agp -DKBUILD_MODNAME=
   nvidia -c -o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_
   os-agp.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-agp.c:24:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-agp.c:24:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.os-i
   nterface.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -W
   strict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -f
   omit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i
   386 -Iinclude/asm-i386/mach-default  -I/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-
   7667-pkg1/usr/src/n
   v -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparen
   theses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD   -Wsign-
   compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODUL
   E  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNV_MA
   JOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667  -UDEBUG -U_DEBUG -D
   NDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE
   _ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DN
   V_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_interface -DKBUILD_MODNAME=n
   vidia -c -o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.tmp_o
   s-interface.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/os-i
   nterface.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-interface.c:26:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-interface.c:26:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     cc -Wp,-MD,/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.os-r
   egistry.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Ws
   trict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fo
   mit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march
   =i386 -Iinclude/asm-i386/mach-default  -I/tmp/selfgz9696/NVIDIA-Linux-x86-1.
   0-7667-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wch
   ar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno
   -common -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES
   -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_NAMES -D__KERNEL
   __ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=7667 
   -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESE
   NT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_PCI_GE
   T_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_registry 
   -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1
   /usr/src/nv/.tmp_os-registry.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg
   1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:46,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-registry.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/nv-linux.h:69,
                    from /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src
   /nv/os-registry.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:242: warning: wrong type argument to increment
     ld -m elf_i386  -r -o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/s
   rc/nv/nvidia.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv-
   kernel.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv.o /tmp
   /selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nv-vm.o /tmp/selfgz969
   6/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/os-agp.o /tmp/selfgz9696/NVIDIA-
   Linux-x86-1.0-7667-pkg1/usr/src/nv/os-interface.o /tmp/selfgz9696/NVIDIA-Lin
   ux-x86-1.0-7667-pkg1/usr/src/nv/os-registry.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.10-5-386/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.10-5-386/Module.sy
   mvers /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nvidia.o
   Warning: could not find /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/s
   rc/nv/.nv-kernel.o.cmd for /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/us
   r/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/.nvid
   ia.mod.o.d -nostdinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wst
   rict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Os     -fom
   it-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=i38
   6 -
   Iinclude/asm-i386/mach-default     -DKBUILD_BASENAME=nvidia -DKBUILD_MODNAME
   =nvidia -DMODULE -c -o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/sr
   c/nv/nvidia.mod.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/
   nvidia.mod.c
     ld -m elf_i386 -r -o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/sr
   c/nv/nvidia.ko /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nvi
   dia.o /tmp/selfgz9696/NVIDIA-Linux-x86-1.0-7667-pkg1/usr/src/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 File exists
-> Kernel messages:
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
   apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
   apm: overridden by ACPI.
   drivers/usb/input/hid-input.c: event field not found
   eth0: no IPv6 routers present
   agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
   agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
   agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
   agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

Please help...

---

### Post by kosmic on 2005-08-06
Why don't you use the apt-get (synaptic) to install the Nvidia Drivers, just do :

sudo apt-get install nvidia-glx nvidia-kernel-common

---

### Post by Stallone on 2005-08-06
ahh, thankyou.

I think that might have solved my problem :)

---

### Post by kosmic on 2005-08-06
[QUOTE=Stallone]ahh, thankyou.

I think that might have solved my problem :)[/QUOTE]


And don't forget after install to go to a console and do the following :

sudo nvidia-glx-config enable

to activate the drivers

---

### Post by LinNewbie on 2005-08-07
I too am having the same kernel problem as Stallone.  kosmic you by-passed Stallone's question by simply telling him how to install the default Nvidia drivers ... which were likely installed during Ubuntu's install.  So if he did as you said, he probably changed nothing  ...

So, Like him, I would like help in getting the Nvidia released 7667 drivers installed.  I have EXACTLY the same kernel issues as Stallone.

I have downloaded all necessary packages and even tried the necessary linker (sudo ln -s /usr/src/linux-2.6.12 /usr/src/linux cd /usr/src/linux).... and here is where I think it failed.  I really do not understand what the "linker" does ... 

Am I trying to link the source folder (/usr/src/linux-source-2.6.10) with what since /usr/src/linux didn't work ...

Any help with this would be appreciated.  And please no arguments concering whether or not I should install the Nvidia released drivers; I just want to learn how! :)

Thanks in advance ...

---

### Post by strikeforce on 2005-08-07
Try this link.

[http://ubuntuforums.org/showthread.php?t=51734](http://ubuntuforums.org/showthread.php?t=51734)

He has a great howto on there.

---

### Post by tseliot on 2005-08-26
[QUOTE=strikeforce]Try this link.

[http://ubuntuforums.org/showthread.php?t=51734](http://ubuntuforums.org/showthread.php?t=51734)

He has a great howto on there.[/QUOTE]
Or you might as well try my HOWTO (it's a step by step guide)

[http://www.ubuntuforums.org/showthread.php?t=57368](http://www.ubuntuforums.org/showthread.php?t=57368) 

Please if you want to ask question about the guide, post them there.

---

