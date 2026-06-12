---
title: "Another nVidia driver thread"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by GOLDfish_74 on 2006-10-20
I have been sifting through this forum for days taking bits of information on how to install nVidia drivers and have been piecing together my n00bilating puzzle together, and just when I thought I had success... 100% YAY -> Failed... WTF?!](*,) 

Building Kernel Module -> 100% - and then...

ERROR: Unable to build the NVIDIA kernel module. [OK]

The command I am running to make this work is:
sudo sh nvidia.run --kernel-source-path /usr/src/linux-headers-2.6.15-27

Note: I changed the driver name to nvidia.run because the original file name was a bitch to type.

Thanks for any help recieved...

>< ))*>GOLDfish<*(( ><

---

### Post by hanzomon4 on 2006-10-20
Which driver version, 9xxxx driver or 8xxxx driver? For the 9xxxx dirver I think you need edgy.

This is what I did for the 9xxx driver, might work with the 8xxxx driver.

1.Download the nvidia driver installer from the nvidia website
2.Switch to vtr 2.... ctrl+alt+F2
3.Kill X.... type this ```
sudo /etc/init.d/gdm stop
```
4.Run the installer... type this ```
 sudo sh Desktop/NVIDIA-Linux-x86-1.0-9626-pkg1.run
``` Note you don't have to finish typing the name of the NVIDIA installer just type NV and press tab.
5.Restart X type ```
sudo /etc/init.d/gdm restart
```

---

### Post by franpa on 2006-10-21
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

that tells you exactly what to type... i also tried doing stuff with drivers from nvidias site but it was to painfull... it tells you how to install them and takes a couple of minutes.

---

### Post by boz on 2006-10-21
> **GOLDfish_74 said:**
> I have been sifting through this forum for days taking bits of information on how to install nVidia drivers and have been piecing together my n00bilating puzzle together, and just when I thought I had success... 100% YAY -> Failed... WTF?!](*,) 

Building Kernel Module -> 100% - and then...

ERROR: Unable to build the NVIDIA kernel module. [OK]

The command I am running to make this work is:
sudo sh nvidia.run --kernel-source-path /usr/src/linux-headers-2.6.15-27

Note: I changed the driver name to nvidia.run because the original file name was a bitch to type.

Thanks for any help recieved...

>< ))*>GOLDfish<*(( ><

Did you follow these instructions (go to the Debian/Ubuntu section at the bottom)?  [nv  forums]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

---

### Post by GOLDfish_74 on 2006-10-22
I have tried all of the ideas suggested, followed all instructions and still getting the same error. I hope someone has some better ideas.

Note: I don't want to use the generic drivers.

Thanks all for trying,
GOLDfish.

---

### Post by hanzomon4 on 2006-10-22
I'll do some looking around and get back to ya

---

### Post by GOLDfish_74 on 2006-10-22
I havent been able to find this same error anywhere. I have read stuff about something to do with "nv" whats that all about?

Regards,
THEfish.

---

### Post by hanzomon4 on 2006-10-22
Post the output of this command ```
cat /var/log/nvidia-installer.log
```

---

### Post by GOLDfish_74 on 2006-10-23
This is the output for the .log file:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Oct 23 15:25:46 2006

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
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-headers-2.6.15-27
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
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-headers-2.6.15-27' as specified
   by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.15-27'
-> Kernel output path: '/usr/src/linux-headers-2.6.15-27'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/linux-headers-2.6.1
   5-27 SYSOUT=/usr/src/linux-headers-2.6.15-27'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/linux-headers-2.6.15-27 SUBDIRS=/tm
   p/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv modules
   mkdir -p /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.tmp_v
   ersions
   
     WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-27/Module.symve
   rs
              is missing; modules will have no dependencies and modversions.
   
   make -f scripts/Makefile.build obj=/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8
   776-pkg2/usr/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /tmp/selfgz5733/NVI
   DIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.n
   v.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.0.3/include -D__KE
   RNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-p
   rototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os
       -fomit-frame-pointer  -mno-red-zone -mcmodel=kernel -pipe -fno-reorder-b
   locks	
    -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-time -mno-sse
   -mno-mmx -mno-sse2 -mno-3dnow -Wdeclaration-after-statement -Wno-pointer-sig
   n -I/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv -Wall -Wimp
   licit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoin
   ter-arith  -Wno-multichar  -Werror -O -fno-common -mno-red-zone -minline-all
   -stringops -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NA
   MES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM -DNVRM -DDYNAMIC_SLI  -DNV
   _MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8776  -UDEBUG -U_DEBUG
   -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_P
   CI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRE
   SENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PF
   N_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE 
   -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz5733/NVIDIA-Li
   nux-x86_64-1.0-8776-pkg2/usr/src/n
   v/.tmp_nv.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/nv.
   c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv.c:14:
   include/linux/cpumask.h: In function ‘__first_cpu’:
   include/linux/cpumask.h:219: warning: signed and unsigned type in conditiona
   l expression
   include/linux/cpumask.h: In function ‘__next_cpu’:
   include/linux/cpumask.h:225: warning: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv.c:14:
   include/linux/nodemask.h: In function ‘__first_node’:
   include/linux/nodemask.h:230: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__next_node’:
   include/linux/nodemask.h:236: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__first_unset_node’:
   include/linux/nodemask.h:254: warning: signed and unsigned type in condition
   al expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:303: warning: wrong type argument to increment
   In file included from include/asm/pci.h:95,
                    from include/linux/pci.h:612,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv.c:14:
   include/asm-generic/pci-dma-compat.h: In function ‘pci_map_page’:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type ‘void *
    used in arithmetic
   In file included from include/linux/compat.h:15,
                    from include/asm/mtrr.h:28,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:104,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv.c:14:
   include/asm/compat.h: In function ‘compat_alloc_user_space’:
   include/asm/compat.h:201: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/asm/compat.h:202: warning: pointer of type ‘void *’ used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.n
   v-vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.0.3/include -D_
   _KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding 
   -Os     -fomit-frame-pointer  -mno-red-zone -mcmodel=kernel -pipe -fno-reord
   er-blocks	 -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-tim
   e -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wdeclaration-after-statement -Wno-
   pointer-sign -I/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv 
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -mno-red-zone -
   m
   inline-all-stringops -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE
   _KERNEL_NAMES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM -DNVRM -DDYNAMIC
   _SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8776  -UDEBU
   G -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRE
   SENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_ME
   SSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -D
   NV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT
    -DMODULE -DKBUILD_BASENAME=nv_vm -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz5
   733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.tmp_nv-vm.o /tmp/selfgz573
   3/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/nv-vm.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/linux/cpumask.h: In function ‘__first_cpu’:
   include/linux/cpumask.h:219: warning: signed and unsigned type in conditiona
   l expression
   include/linux/cpumask.h: In function ‘__next_cpu’:
   include/linux/cpumask.h:225: warning: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/linux/nodemask.h: In function ‘__first_node’:
   include/linux/nodemask.h:230: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__next_node’:
   include/linux/nodemask.h:236: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__first_unset_node’:
   include/linux/nodemask.h:254: warning: signed and unsigned type in condition
   al expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:303: warning: wrong type argument to increment
   In file included from include/asm/pci.h:95,
                    from include/linux/pci.h:612,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/asm-generic/pci-dma-compat.h: In function ‘pci_map_page’:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type ‘void *
    used in arithmetic
   In file included from include/linux/compat.h:15,
                    from include/asm/mtrr.h:28,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:104,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-vm.c:14:
   include/asm/compat.h: In function ‘compat_alloc_user_space’:
   include/asm/compat.h:201: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/asm/compat.h:202: warning: pointer of type ‘void *’ used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.o
   s-agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.0.3/include -D
   __KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding
   -Os     -fomit-frame-pointer  -mno-red-zone -mcmodel=kernel -pipe -fno-reord
   er-blocks	 -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-tim
   e -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wdeclaration-after-statement -Wno-
   pointer-sign -I/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv 
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -mno-red-zone -
   minline-all-stringops -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOS
   E_KERNEL_NAMES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM -DNVRM -DDYNAMI
   C_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8776  -UDEB
   UG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PR
   ESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SY
   SCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_P
   RESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_
   PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=os_agp -DK
   BUILD_MODNAME=nvidia -c -o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2
   /usr/src/nv/.tmp_os-agp.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/
   usr/src/nv/os-agp.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-agp.c:24:
   include/linux/cpumask.h: In function ‘__first_cpu’:
   include/linux/cpumask.h:219: warning: signed and unsigned type in conditiona
   l expression
   include/linux/cpumask.h: In function ‘__next_cpu’:
   include/linux/cpumask.h:225: warning: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-agp.c:24:
   include/linux/nodemask.h: In function ‘__first_node’:
   include/linux/nodemask.h:230: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__next_node’:
   include/linux/nodemask.h:236: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__first_unset_node’:
   include/linux/nodemask.h:254: warning: signed and unsigned type in condition
   al expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-agp.c:24:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-agp.c:24:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:303: warning: wrong type argument to increment
   In file included from include/asm/pci.h:95,
                    from include/linux/pci.h:612,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-agp.c:24:
   include/asm-generic/pci-dma-compat.h: In function ‘pci_map_page’:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type ‘void *
    used in arithmetic
   In file included from include/linux/compat.h:15,
                    from include/asm/mtrr.h:28,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:104,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-agp.c:24:
   include/asm/compat.h: In function ‘compat_alloc_user_space’:
   include/asm/compat.h:201: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/asm/compat.h:202: warning: pointer of type ‘void *’ used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.o
   s-interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.0.3/incl
   ude -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef 
   -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreest
   anding -Os     -fomit-frame-pointer  -mno-red-zone -mcmodel=kernel -pipe -fn
   o-reorder-blocks	 -Wno-sign-compare
    -fno-asynchronous-unwind-tables -funit-at-a-time -mno-sse -mno-mmx -mno-sse
   2 -mno-3dnow -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz57
   33/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-ty
   pe -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-m
   ultichar  -Werror -O -fno-common -mno-red-zone -minline-all-stringops -MD   
   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOSE_KERNEL_NAMES -D__KERNEL__ 
   -DMODULE  -mcmodel=kernel -DNTRM -DNVRM -DDYNAMIC_SLI  -DNV_MAJOR_VERSION=1 
   -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8776  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SI
   GNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRE
   SENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CH
   OOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT 
   -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAM
   E=os_interface -DKBUILD_MODNAME=nvidia -c -o /tmp/selfgz5733/NVIDIA-Linux-x8
   6_64-1.0-8776-pkg2/usr/src/nv/.tmp_o
   s-interface.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/o
   s-interface.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-interface.c:26:
   include/linux/cpumask.h: In function ‘__first_cpu’:
   include/linux/cpumask.h:219: warning: signed and unsigned type in conditiona
   l expression
   include/linux/cpumask.h: In function ‘__next_cpu’:
   include/linux/cpumask.h:225: warning: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-interface.c:26:
   include/linux/nodemask.h: In function ‘__first_node’:
   include/linux/nodemask.h:230: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__next_node’:
   include/linux/nodemask.h:236: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__first_unset_node’:
   include/linux/nodemask.h:254: warning: signed and unsigned type in condition
   al expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-interface.c:26:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-interface.c:26:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:303: warning: wrong type argument to increment
   In file included from include/asm/pci.h:95,
                    from include/linux/pci.h:612,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-interface.c:26:
   include/asm-generic/pci-dma-compat.h: In function ‘pci_map_page’:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type ‘void *
    used in arithmetic
   In file included from include/linux/compat.h:15,
                    from include/asm/mtrr.h:28,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:104,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-interface.c:26:
   include/asm/compat.h: In function ‘compat_alloc_user_space’:
   include/asm/compat.h:201: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/asm/compat.h:202: warning: pointer of type ‘void *’ used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.o
   s-registry.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.0.3/inclu
   de -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -
   Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreesta
   nding -Os     -fomit-frame-pointer  -mno-red-zone -mcmodel=kernel -pipe -fno
   -reorder-blocks	 -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at
   -a-time -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wdeclaration-after-statement
   -Wno-pointer-sign -I/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/sr
   c/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpa
   rent
   heses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -mno-red-zone 
   -minline-all-stringops -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOO
   SE_KERNEL_NAMES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM -DNVRM -DDYNAM
   IC_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHLEVEL=8776  -UDE
   BUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_BRIDGE_AGPGART_P
   RESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_PRESENT -DNV_PM_
   MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSERT_PAGE_PRESENT 
   -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_VMAP_4_PRESE
   NT  -DMODULE -DKBUILD_BASENAME=os_registry -DKBUILD_MODNAME=nvidia -c -o /tm
   p/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.tmp_os-registry.o
   /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/os-registry.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-registry.c:14:
   include/linux/cpumask.h: In function ‘__first_cpu’:
   include/linux/cpumask.h:219: warning: signed and unsigned type in conditiona
   l expression
   include/linux/cpumask.h: In function ‘__next_cpu’:
   include/linux/cpumask.h:225: warning: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-registry.c:14:
   include/linux/nodemask.h: In function ‘__first_node’:
   include/linux/nodemask.h:230: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__next_node’:
   include/linux/nodemask.h:236: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__first_unset_node’:
   include/linux/nodemask.h:254: warning: signed and unsigned type in condition
   al expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-registry.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-registry.c:14:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:303: warning: wrong type argument to increment
   In file included from include/asm/pci.h:95,
                    from include/linux/pci.h:612,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-registry.c:14:
   include/asm-generic/pci-dma-compat.h: In function ‘pci_map_page’:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type ‘void *
    used in arithmetic
   In file included from include/linux/compat.h:15,
                    from include/asm/mtrr.h:28,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:104,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/os-registry.c:14:
   include/asm/compat.h: In function ‘compat_alloc_user_space’:
   include/asm/compat.h:201: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/asm/compat.h:202: warning: pointer of type ‘void *’ used in arit
   hmetic
     cc -Wp,-MD,/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.n
   v-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.0.3/include -D
   __KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding
   -Os     -fomit-frame-pointer  -mno-red-zone -mcmodel=kernel -pipe -fno-reord
   er-blocks	 -Wno-sign-compare -fno-asynchronous-unwind-tables -funit-at-a-tim
   e -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wdeclaration-after-statement -Wno-
   pointer-sign -I/tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv 
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -mno-red-zone -
   minline-all-stringops -MD   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOS
   E_KERNEL_NAMES -D__KERNEL__ -DMODULE  -mcmodel=kernel -DNTRM -DNVRM -DDYNAMI
   C_SLI  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_PATCHL
   EVEL=8776  -UDEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_MULTIPLE_B
   RIDGE_AGPGART_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_SYSCTL_MAX_MAP_COUNT_P
   RESENT -DNV_PM_MESSAGE_T_PRESENT -DNV_PCI_CHOOSE_STATE_PRESENT -DNV_VM_INSER
   T_PAGE_PRESENT -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -D
   NV_VMAP_4_PRESENT  -DMODULE -DKBUILD_BASENAME=nv_i2c -DKBUILD_MODNAME=nvidia
   -c -o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/.tmp_nv-i
   2c.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/nv-i2c.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-i2c.c:8:
   include/linux/cpumask.h: In function ‘__first_cpu’:
   include/linux/cpumask.h:219: warning: signed and unsigned type in conditiona
   l expression
   include/linux/cpumask.h: In function ‘__next_cpu’:
   include/linux/cpumask.h:225: warning: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/sched.h:17,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-i2c.c:8:
   include/linux/nodemask.h: In function ‘__first_node’:
   include/linux/nodemask.h:230: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__next_node’:
   include/linux/nodemask.h:236: warning: signed and unsigned type in condition
   al expression
   include/linux/nodemask.h: In function ‘__first_unset_node’:
   include/linux/nodemask.h:254: warning: signed and unsigned type in condition
   al expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:20,
                    from include/linux/module.h:10,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:51,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-i2c.c:8:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:485,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-i2c.c:8:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:303: warning: wrong type argument to increment
   In file included from include/asm/pci.h:95,
                    from include/linux/pci.h:612,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:76,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-i2c.c:8:
   include/asm-generic/pci-dma-compat.h: In function ‘pci_map_page’:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type ‘void *
    used in arithmetic
   In file included from include/linux/compat.h:15,
                    from include/asm/mtrr.h:28,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-linux.h:104,
                    from /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-i2c.c:8:
   include/asm/compat.h: In function ‘compat_alloc_user_space’:
   include/asm/compat.h:201: warning: pointer of type ‘void *’ used in arit
   hmetic
   include/asm/compat.h:202: warning: pointer of type ‘void *’ used in arit
   hmetic
     ld -m elf_x86_64  -r -o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/
   usr/src/nv/nvidia.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/sr
   c/nv/nv-kernel.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/n
   v/nv.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/
   src/nv/nv-vm.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/
   os-agp.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/os-int
   erface.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/os-reg
   istry.o /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/nv-i2c.
   o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.15-27/scripts/Makefile.modpost
     scripts/mod/modpost -m  -i /usr/src/linux-headers-2.6.15-27/Module.symvers
   /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/nvidia.o
   /bin/sh: scripts/mod/modpost: No such file or directory
   make[3]: *** [__modpost] Error 127
   make[2]: *** [modules] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.


```

I hope this helps!

GOLDfish!

---

### Post by GOLDfish_74 on 2006-10-23
Could it have something to do with which user I am trying to use. I have used both "root" and my login user accounts and both return the same error, should I try a different user account?

Regards,
THEfish!

---

### Post by hanzomon4 on 2006-10-23
It has something to with this part at the end. >  Building modules, stage 2.
   [B]make -rR -f /usr/src/linux-headers-2.6.15-27/scripts/Makefile.modpost
     scripts/mod/modpost -m  -i /usr/src/linux-headers-2.6.15-27/Module.symvers
   /tmp/selfgz5733/NVIDIA-Linux-x86_64-1.0-8776-pkg2/usr/src/nv/nvidia.o
  [COLOR="Red"]/bin/sh: scripts/mod/modpost: No such file or directory[/COLOR][/B]
   make[3]: *** [__modpost] Error 127
   make[2]: *** [modules] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).
I'm getting closer, you should have a [COLOR="Red"]**/usr/src/linux-headers-2.6.15-27/scripts/mod/modpost**[/COLOR]

Post the output of this command ```
ls -l /usr/src/linux-headers-2.6.15-27/scripts/mod/modpost
``` 
If you don't getting anything back then thats the source of the problem, I'll see how to go about fixing that.

---

### Post by tseliot on 2006-10-23
Try Method 2 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Or use Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Or my testing repos:
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by GOLDfish_74 on 2006-10-24
> **hanzomo said:**
> It has something to with this part at the end. 
I'm getting closer, you should have a [COLOR="Red"]**/usr/src/linux-headers-2.6.15-27/scripts/mod/modpost**[/COLOR]

Post the output of this command ```
ls -l /usr/src/linux-headers-2.6.15-27/scripts/mod/modpost
``` 
If you don't getting anything back then thats the source of the problem, I'll see how to go about fixing that.

The output was:
```
ls: /usr/src/linux-headers-2.6.15-27/scripts/mod/modpost: No such file or directory
```

How can I fix this issue?

Regards,
THEfish!

---

### Post by GOLDfish_74 on 2006-10-24
I'm pretty sure Envy was the answer to all of my problems, will post back if problems return!

Thanks all for your help, every little bit was a learning curve and I appreciate all of the help along the way, even if some of it didnt work!

Thanks again,
>< ))*>GOLDfish!<*(( ><

---

### Post by hanzomon4 on 2006-10-24
Glad you got it working.

---

### Post by labradorg13 on 2006-12-06
Where i can download my Video Card Driver and How to install it?

Graphics Card : GeForce2 MX400/400 (64mb)...

---

