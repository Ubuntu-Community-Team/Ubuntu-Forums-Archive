---
title: "low latency kernel for optimal performance for Enemy Territory Quake Wars?"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by userkwokcmscv on 2008-10-16
Installed Ubuntu 8.04 and nvidia 177.80 -display driver.

From ETQW Readme-file:

> You need a low latency kernel for optimal performance (this applies to both client and server installations). Make sure your kernel
is configured with CONFIG_HZ_1000=y. You should also enable other low latency settings, such as the various preemption settings.

How do I get low latency kernel?

I don't know how to compile or configure kernel for ETQW.

Do I have to uninstall and reinstall Nvidia drivers and Quake Wars after new kernel? :confused:

Help!

---

### Post by logos34 on 2008-10-16
> **userkwokcmscv said:**
> How do I get low latency kernel?

You want the ubuntu real-time kernel pkg:

[B]sudo apt-get install linux-rt 
[/B] 
The timer resolution/freq will already be set to 1000 Hz.
 
>  Do I have to uninstall and reinstall Nvidia drivers and Quake Wars after new kernel?

Yes, because the kernel interface module of the graphics driver is compiled against the kernel headers.  So you need this too:

**sudo apt-get **[B]linux-headers-2.6.24-21-rt
[/B]
You may need to point the interactive installer to 'kernel-source-path=/usr/src/linux-headers-2.6.24-21-rt'

> "You can specify the location of the kernel source tree (or headers) when you install the NVIDIA driver using the --kernel-source-path command line option (see **sh NVIDIA-Linux-x86-177.80-pkg1.run --advanced-options** for details)."
[http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-08.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-08.html)


good luck

---

### Post by userkwokcmscv on 2008-10-17
> **logos34 said:**
> 
**sudo apt-get **[B]linux-headers-2.6.24-21-rt
[/B]

Your command didn't work, so i edited it to this:
**sudo apt-get install linux-headers-2.6.24-21-rt**

On next restart sound card sends some weird wobbly sound?!? :-k

> **logos34 said:**
> 
You may need to point the interactive installer to 'kernel-source-path=/usr/src/linux-headers-2.6.24-21-rt'

I inserted these commands to the terminal:

[B]ctrl+alt+F1

/etc/init.d/gdm stop

sh NVIDIA-Linux-x86-177.80-pkg1.run --uninstall

sh NVIDIA-Linux-x86-177.80-pkg1.run --kernel-source-path=/usr/src/linux-headers-2.6.24-21-rt/[/B]

Then Nvidia installer outputs some error. :confused:

Restarted, and I got low-res 800x600 screen. I'm typing this post from that low-res screen.

If I can't install Nvidia drivers with this real-time kernel, could you tell how to revert back to original setup, please?

It's pain using 800x600 screen.

Log file from /var/log/nvidia-installer.log

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Oct 17 08:39:37 2008
installer version: 1.0.7

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
  no cc version check     : false
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
  kernel source path      : /usr/src/linux-headers-2.6.24-21-rt/
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 177.80.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.24-21-rt/' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.24-21-rt/'
-> Kernel output path: '/usr/src/linux-headers-2.6.24-21-rt/'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.2
   4-21-rt/ SYSOUT=/usr/src/linux-headers-2.6.24-21-rt/'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.24-21-rt/ SUBDIRS

   =/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_versio
   ns ; rm -f /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_vers
   ions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-p
   kg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nv.o.d
    -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL__  
   -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototyp
   es -Wno-trigraphs -fno-strict-aliasing
    -fno-common -Werror-implicit-function-declaration -O2 -pipe -msoft-float -m
   regparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i586 -mtu
   ne=generic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mac
   h-default -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-
   statement -Wno-pointer-sign   -I/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1
   /usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscrip
   ts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare
   -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\
   "177.80\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD
   _BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz9818
   /NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nv.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nv-vm.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNEL
   __  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prot
   otypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-func
   tion-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumu
   late-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g 
   -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tm
   p/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit -Wretu
   rn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -W
   no-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_DEBUG -DNDEB
   UG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"
   KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9818/NVIDIA-Linux-x86-17
   7.80-pkg1/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pk
   g1/usr/src/nv/nv-vm.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.os-agp
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-
   struct-return -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffre
   estanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit
   -frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-p
   ointer-sign   -I/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wal
   l -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses
   -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -
   Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBU
   G -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9818/N
   VIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_os-agp.o /tmp/selfgz9818/NVIDIA-
   Linux-x86-177.80-pkg1/usr/src/nv/os-agp.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.os-int
   erface.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D_
   _KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retu
   rn -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -
   maccumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-poin
   ter -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign
     -I/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit
   -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D
   __KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_D
   EBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(o
   s_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9818/N
   VIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_os-interface.o /tmp/selfgz9818/N
   VIDIA-Linux-x86-177.80-pkg1/usr/src/nv/os-interface.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.os-reg
   istry.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__
   KERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implici
   t-function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-retur
   n -mpreferred
   -stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccumulate-ou
   tgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g  -fno-s
   tack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/tmp/self
   gz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -
   DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_DEBUG -DNDEBUG  -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"K
   BUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9818/NVIDIA-Linux-x86-177
   .80-pkg1/usr/src/nv/.tmp_os-registry.o /tmp/selfgz9818/NVIDIA-Linux-x86-177.

   80-pkg1/usr/src/nv/os-registry.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nv-i2c
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -maccum
   ulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer -g
    -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign   -I/t
   mp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv -Wall -Wimplicit -Wret
   urn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -
   Wno-multichar -Werror -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80\" -UDEBUG -U_DEBUG -
   DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)
   "  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz9818/NVIDIA-Linux-
   x86-177.80-pkg1/usr/src/nv/.tmp_nv-i2c.o /tmp/selfgz9818/NVIDIA-Linux-x86-17
   7.80-pkg1/usr/src/nv/nv-i2c.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nvacpi
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__KERNE
   L__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-pro
   totypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-fun
   ction-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return -mp
   referred-stack-boundary=2  -march=i586 -mtune=gener
   ic -ffreestanding -maccumulate-outgoing-args   -Iinclude/asm-x86/mach-defaul
   t -fomit-frame-pointer -g  -fno-stack-protector -Wdeclaration-after-statemen
   t -Wno-pointer-sign   -I/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -MD   -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"177.80
   \" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENA
   ME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/sel
   fgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.tmp_nvacpi.o /tmp/selfgz981
   8/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nvacpi.c
   In file included from include/linux/list.h:8,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:85,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:53,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:19,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/asm/dma-mapping_32.h:5,
                    from include/asm/dma-mapping.h:2,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:88,
                    from include/linux/pci.h:796,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nv-linux.h:86,
                    from /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/n
   v/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:293: warning: pointer of type ‘void *’ used 
   in arithmetic
     ld -m elf_i386 -m elf_i386   -r -o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/s
   rc/nv/nv-kernel.o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nv
   .o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nv-vm.o /tmp/self
   gz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/os-agp.o /tmp/selfgz9818/NVID
   IA-Linux-x86-177.80-pkg1/usr/src/nv/os-interface.o /tmp/selfgz9818/NVIDIA-Li
   nux-x86-177.80-pkg1/usr/src/nv/os-registry.o /tmp/selfgz9818/NVIDIA-Linux-x8
   6-177.80-pkg1/usr/src/nv/nv-i2c.o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pk
   g1/usr/src/nv/nvacpi.o
     Building modules, stage 2.
   make -f /usr/src/linux-headers-2.6.24-21-rt/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.24-21-rt/Module.sy
   mvers -I /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/Module.symv
   ers -o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/Module.symver
   s -w -s
   WARNING: could not find /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src
   /nv/.nv-kernel.o.cmd for /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/sr
   c/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/.nvidia
   .mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.3/include -D__K
   ERNEL__  -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit
   -function-declaration -O2 -pipe -msoft-float -mregparm=3 -freg-struct-return
   -mpreferred-stack-boundary=2  -march=i586 -mtune=generic -ffreestanding -mac
   cumulate-outgoing-args   -Iinclude/asm-x86/mach-default -fomit-frame-pointer
   -g  -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sign    
   -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_M
   ODNAME=KBUILD_STR(nvidia)" -DMODULE -c -o /tmp/selfgz9818/NVIDIA-Linux-x86-1
   77.80-pkg1/usr/src/nv/nvidia.mod.o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-p
   kg1/usr/src/nv/nvidia.mod.c
     ld -m elf_i386 -r -m elf_i386  --build-id -o /tmp/selfgz9818/NVIDIA-Linux-
   x86-177.80-pkg1/usr/src/nv/nvidia.ko /tmp/selfgz9818/NVIDIA-Linux-x86-177.80
   -pkg1/usr/src/nv/nvidia.o /tmp/selfgz9818/NVIDIA-Linux-x86-177.80-pkg1/usr/s
   rc/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Invalid module format
-> Kernel messages:
   [   51.331751] NET: Registered protocol family 31
   [   51.331756] Bluetooth: HCI device and connection manager initialized
   [   51.331760] Bluetooth: HCI socket layer initialized
   [   51.351734] Bluetooth: L2CAP ver 2.9
   [   51.351739] Bluetooth: L2CAP socket layer initialized
   [   51.395783] Bluetooth: RFCOMM socket layer initialized
   [   51.395799] Bluetooth: RFCOMM TTY layer initialized
   [   51.395801] Bluetooth: RFCOMM ver 1.8
   [   91.501276] NET: Registered protocol family 10
   [   91.501494] lo: Disabled Privacy Extensions
   [   91.502159] ADDRCONF(NETDEV_UP): wlan0: link is not ready
   [   95.389184] CPU0 attaching NULL sched-domain.
   [   95.389193] CPU1 attaching NULL sched-domain.
   [   95.402051] CPU0 attaching sched-domain:
   [   95.402058]  domain 0: span 03
   [   95.402060]   groups: 01 02
   [   95.402064] CPU1 attaching sched-domain:
   [   95.402065]  domain 0: span 03
   [   95.402067]   groups: 02 01
   [   98.435520] eth0: no IPv6 routers present
   [   98.609513] UDF-fs: Partition marked readonly; forcing readonly mount
   [   98.654122] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume
   'ETQWDVD', timestamp 2007/08/26 03:21 (10b4)
   [  309.574218] nvidia: disagrees about version of symbol struct_module
   [  545.298420] nvidia: disagrees about version of symbol struct_module
   [  573.189622] nvidia: disagrees about version of symbol struct_module
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by logos34 on 2008-10-17
> **userkwokcmscv said:**
> If I can't install Nvidia drivers with this real-time kernel, could you tell how to revert back to original setup, please?

Uninstall the 177.80 driver, and try the 169.12 (nvidia-glx-new), which is in the repos:

> [http://ubuntuguide.org/wiki/Ubuntu:Hardy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Hardy#NVidia_Driver) 

You can also install this package from Synaptic Package Manager (which I did.) 
 
[LIST]
[*]Go to ***System > Administration > Restricted Drivers Manager*** and turn on the driver.
[/LIST]
 
[LIST]
[*]Reboot
[/LIST]
 
[LIST]
[*]Some users may receive an error screen: "The software source for the packsge nvidia-glx-new is not enabled." This can be overcome by going to ***System > Administration > Software Sources*** and ticking all the boxes under the heading "Downloadable from the Internet", click close and then allow Ubuntu to reload the package lists. The NVidia drivers can then be enabled using the method above.
[/LIST]
 
[LIST]
[*]You can optionally prevent showing NVidia logo on startup by:
[/LIST]
 sudo nvidia-xconfig --no-logo

---

