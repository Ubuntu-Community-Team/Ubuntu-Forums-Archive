---
title: "Purple Screen After Kernel Upgrade 2.6.39"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by terrykiwi83 on 2011-07-10
Hi,

I have just upgraded to kernel 2.6.39 from 2.6.38 and when I boot into the new 2.6.39 I am left stuck on just a purple screen, nothing else just solid purple. I am still able to go into the old kernel (hence posting here) but not able to access 2.6.39.

I have a suspicion it has something to do with the graphics, to be exact the nVidia driver which I installed from nvidia.com in kernel 2.6.38. Is it possible that kernel 2.6.39 is trying to use these drivers and that is causing the purple screen.

Any ideas on how to troubleshoot this one? 

Cheers

---

### Post by MAFoElffen on 2011-07-10
> **terrykiwi83 said:**
> Hi,

I have just upgraded to kernel 2.6.39 from 2.6.38 and when I boot into the new 2.6.39 I am left stuck on just a purple screen, nothing else just solid purple. I am still able to go into the old kernel (hence posting here) but not able to access 2.6.39.

I have a suspicion it has something to do with the graphics, to be exact the nVidia driver which I installed from nvidia.com in kernel 2.6.38. Is it possible that kernel 2.6.39 is trying to use these drivers and that is causing the purple screen.

Any ideas on how to troubleshoot this one? 

Cheers

Edit:: After a bit of looking around I found [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
On the nvidia driver, is it the Proprietary through Additional Drivers or through NVidia's nvidia-installer?  Did you install the linux-headers-2.6.39 files?

---

### Post by terrykiwi83 on 2011-07-10
I installed nVidia's nvidia-installer from their website, and yes I installed the linux-headers files :)

---

### Post by MAFoElffen on 2011-07-10
> **terrykiwi83 said:**
> I installed nVidia's nvidia-installer from their website, and yes I installed the linux-headers files :)
Can you post the nvidia-installer log file '/var/log/nvidia-installer.log'?

And these files if present:
/etc/X11/xorg.conf
/var/log/xorg.0.log
~/.xsession-errors

And as it is a problem after a kernel change... The output from:
```
[FONT=monospace]
[/FONT]uname -s -r && unity --version && cat /etc/lsb-release && /usr/lib/nux/unity_support_test -p 

```

---

### Post by terrykiwi83 on 2011-07-10
Am assuming you want me to post these from within 2.6.38 as I can't access 2.6.39?

Here goes:

/var/log/nvidia-installer.log

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Wed Jun 22 14:11:14 2011
installer version: 275.09.07

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : false
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  force compat32 tls                 : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  compat32 install chroot            : (not specified)
  compat32 install prefix            : (not specified)
  compat32 install libdir            : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 275.09.07.
-> Running distribution scripts
   executing: '/usr/lib/nvidia/pre-install'...
-> done.
-> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.38-8-generic/build'
-> Kernel output path: '/lib/modules/2.6.38-8-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.38-8-generic/bu
   ild SYSOUT=/lib/modules/2.6.38-8-generic/build'...
   NVIDIA: calling KBUILD...
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/generated/autoconf.h or include/config/auto.conf are
   missing.";\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_versions 
   ; rm -f /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.0
   9.07/kernel
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv.o.d  -
   nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/inclu
   de  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude  -i
   nclude include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wu
   ndef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -We
   rror-implicit-function-declara
   tion -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=ge
   neric -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-a
   rgs -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCON
   FIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asy
   nchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-large
   r-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclar
   ation-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stac
   k -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel 
   -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DN
   VRM -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mc
   model=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KB
   UILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /
   tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_nv.o /tmp/selfgz255
   7/NVIDIA-Linux-x86_64-275.09.07/kern
   el/nv.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v.c:13:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v.c:13:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-2.6.
   38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.0
   9.07/kernel/nv.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv-chrdev
   .o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.
   2/include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iincl
   ude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -W
   all -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-com
   mon -Werror-implicit-function-declaration -Wno-format-security -fno-delete-n
   ull-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fu
   nit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVE
   Q=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-
   tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-
   omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-state
   ment -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_G
   OTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel -Wall -MD -Wsign-
   compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_
   STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcmodel=kernel -UDE
   BUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBU
   ILD_STR(nv_chrdev)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz
   2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_nv-chrdev.o /tmp/selfgz2557/N
   VIDIA-Linux-x86_64-275.09.07/kernel/nv-chrdev.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-chrdev.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-chrdev.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-chrdev.o != "scripts/mod/empty.o" ]; then /usr/src/linux-heade
   rs-2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_6
   4-275.09.07/kernel/nv-chrde
   v.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv-mlock.
   o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2
   /include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclu
   de  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wa
   ll -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-comm
   on -Werror-implicit-function-declaration -Wno-format-security -fno-delete-nu
   ll-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -fun
   it-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 
   -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVE
   Q=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mm
   x -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno
   -optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign 
   -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/N
   VIDIA-Linux-x86_64-275
   .09.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL_
   _ -DMODULE -DNVRM -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mn
   o-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_ST
   R(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mlock)"  -D"KBUILD_MODNAME=KBUILD_
   STR(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp
   _nv-mlock.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-mlock.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-mlock.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-mlock.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-mlock.o != "scripts/mod/empty.o" ]; then /usr/src/linux-header
   s-2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64
   -275.09.07/kernel/nv-mlock.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv-procfs
   .o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.
   2/include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iincl
   ude  -include include/generated/autoco
   nf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-t
   rigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declarat
   ion -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=gen
   eric -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-ar
   gs -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONF
   IG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asyn
   chronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger
   -than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclara
   tion-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack
   -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel -W
   all -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVR
   M -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcmo
   del=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUI
   LD_BASENAME=KBUILD_STR(nv_procfs)" 
    -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x8
   6_64-275.09.07/kernel/.tmp_nv-procfs.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-2
   75.09.07/kernel/nv-procfs.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-procfs.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-procfs.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-procfs.o != "scripts/mod/empty.o" ]; then /usr/src/linux-heade
   rs-2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_6
   4-275.09.07/kernel/nv-procfs.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv-userma
   p.o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5
   .2/include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinc
   lude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration -Wno-format-security -fno-delete-
   null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -f
   unit-a
   t-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCO
   NFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 
   -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -m
   no-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-opt
   imize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno
   -strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDI
   A-Linux-x86_64-275.09.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno
   -error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"275.09.07\" -Wno-u
   nused-function -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMO
   DULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_usermap)"  -D"KB
   UILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-2
   75.09.07/kernel/.tmp_nv-usermap.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-usermap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-usermap.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-usermap.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-head
   ers-2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_
   64-275.09.07/kernel/nv-usermap.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv_gvi.o.
   d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/i
   nclude  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude
    -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-
   pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-
   at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DC
   ONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1
   -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -m
   no-sse2 -mno-3dnow -Wframe-larger-than=1
   024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-af
   ter-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_H
   AVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel -Wall -M
   D -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV
   _VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcmodel=ke
   rnel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BAS
   ENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/
   selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_nv_gvi.o /tmp/selfgz255
   7/NVIDIA-Linux-x86_64-275.09.07/kernel/nv_gvi.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v_gvi.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v_gvi.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv_gvi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-
   2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-2
   75.09.07/kernel/nv_gvi.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv-vm.o.d
    -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/inc
   lude  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude  
   -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -
   Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -
   Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-p
   ointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-a
   t-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCO
   NFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 
   -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -m
   no-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-opt
   imize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno
   -strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDI
   A-Linux-x86_64-275.09.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno
   -error -D__KERNEL__ -DMODULE -DNV
   RM -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcm
   odel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBU
   ILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o
   /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_nv-vm.o /tmp/selfg
   z2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-vm.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-vm.c:14:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-vm.c:14:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
   /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-vm.c: In function â€
   ˜nv_sg_map_bufferâ€™:
   /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-vm.c:151:23: warning
   : assignment makes integer from pointer without a cast
   /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-vm.c:236:1: warning:
   label â€˜doneâ€™ defined but not used
   /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-vm.c:144:16: warning
   : unused variable â€˜countâ€™
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-vm.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-2
   .6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-27
   5.09.07/kernel/nv-vm.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.os-agp.o.
   d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/i
   nclude  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude
    -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-
   pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-
   at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DC
   ONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1
   -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -m
   no-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-opt
   imize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno
   -strict-overflow -fconserve-stack -DCC
   _HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel -Wall 
   -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -D
   NV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcmodel=
   kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tm
   p/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_os-agp.o /tmp/selfgz2
   557/NVIDIA-Linux-x86_64-275.09.07/kernel/os-agp.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-agp.c:24:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-agp.c:24:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/os-agp.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-
   2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-2
   75.09.07/kernel/os-agp.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.os-interf
   ace.o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4
   .5.2/include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Ii
   nclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__
   -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-c
   ommon -Werror-implicit-function-declaration -Wno-format-security -fno-delete
   -null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -
   funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI
   =1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXS
   AVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno
   -mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -
   fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-si
   gn -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz255
   7/NVIDIA-Linux-x86_64-275.09.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qu
   al -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"275.09.07\"
   -Wno-unused-function -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG
    -DMODULE  -D"KBUILD_STR(s)=#
   s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_ST
   R(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_o
   s-interface.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/os-interf
   ace.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-interface.c:26:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-interface.c:26:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/os-interface.o != "scripts/mod/empty.o" ]; then /usr/src/linux-he
   aders-2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x8
   6_64-275.09.07/kernel/os-interface.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.os-smp.o.
   d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/i
   nclude  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude
    -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-
   pointer-checks 
   -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -macc
   umulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SI
   GNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overfl
   ow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64
   -275.09.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KER
   NEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function
   -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD
   _STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_smp)"  -D"KBUILD_MODNAME=KBUILD
   _STR(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tm
   p_os-smp.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/os-smp.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-smp.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-smp.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/os-smp.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-
   2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-2
   75.09.07/kernel/os-smp.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.os-userma
   p.o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5
   .2/include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinc
   lude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration -Wno-format-security -fno-delete-
   null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -f
   unit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=
   1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSA
   VEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-
   mmx -mno
   -sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optim
   ize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-s
   trict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-
   Linux-x86_64-275.09.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-e
   rror -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"275.09.07\" -Wno-unu
   sed-function -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODU
   LE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_usermap)"  -D"KBUI
   LD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275
   .09.07/kernel/.tmp_os-usermap.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.0
   7/kernel/os-usermap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-usermap.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-usermap.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/os-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/linux-head
   ers-2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_
   64-275.09.07/kernel/os-usermap.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.os-regist
   ry.o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.
   5.2/include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iin
   clude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ 
   -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-c
   ommon -Werror-implicit-function-declaration -Wno-format-security -fno-delete
   -null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -
   funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI
   =1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXS
   AVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno
   -mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -
   fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-si
   gn -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz255
   7/NVIDIA-Linux-x86_64-275.09.07/kernel -Wall
    -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -
   DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcmodel
   =kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_
   BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c 
   -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_os-registry.o /
   tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/os-registry.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-registry.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/o
   s-registry.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/os-registry.o != "scripts/mod/empty.o" ]; then /usr/src/linux-hea
   ders-2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86
   _64-275.09.07/kernel/os-registry.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv-cray.o
   .d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/
   include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclud
   e  -include include/generated/autoco
   nf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-t
   rigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declarat
   ion -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=gen
   eric -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-ar
   gs -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONF
   IG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asyn
   chronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger
   -than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclara
   tion-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack
   -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel -W
   all -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVR
   M -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcmo
   del=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUI
   LD_BASENAME=KBUILD_STR(nv_cray)"  -
   D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_
   64-275.09.07/kernel/.tmp_nv-cray.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.0
   9.07/kernel/nv-cray.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-cray.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-cray.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-cray.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers
   -2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-
   275.09.07/kernel/nv-cray.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nv-i2c.o.
   d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/i
   nclude  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude
    -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-
   pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-
   at-a-time -maccumul
   ate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL
   _FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-co
   mpare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow
   -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls
   -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fc
   onserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.0
   9.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ 
   -DMODULE -DNVRM -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-
   red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(
   s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(
   nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.tmp_nv-
   i2c.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-i2c.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-i2c.c:8:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-i2c.c:8:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nv-i2c.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-
   2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-2
   75.09.07/kernel/nv-i2c.o"; fi; fi;
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nvacpi.o.
   d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/i
   nclude  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinclude
    -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall 
   -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common 
   -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-
   pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-
   at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DC
   ONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1
   -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -m
   no-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-opt
   imize-siblin
   g-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-over
   flow -fconserve-stack -DCC_HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_
   64-275.09.07/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__K
   ERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"275.09.07\" -Wno-unused-functi
   on -mno-red-zone -mcmodel=kernel -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBU
   ILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBU
   ILD_STR(nvidia)" -c -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/
   .tmp_nvacpi.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nvacpi.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:55,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:39,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   vacpi.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
   In file included from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/uaccess.h:573:0,
                    from include/linux/poll.h:14,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-linux.h:98,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   vacpi.c:15:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h: I
   n function â€˜copy_from_userâ€™:
   /usr/src/linux-headers-2.6.38-8-generic/arch/x86/include/asm/uaccess_64.h:54
   :6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09
   .07/kernel/nvacpi.o != "scripts/mod/empty.o" ]; then /usr/src/linux-headers-
   2.6.38-8-generic/scripts/recordmcount "/tmp/selfgz2557/NVIDIA-Linux-x86_64-2
   75.09.07/kernel/nvacpi.o"; fi; fi;
     ld -m elf_x86_64   -r -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/ker
   nel/nvidia.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-kernel.
   o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv.o /tmp/selfgz2557/
   NVIDIA-Linux-x86_64-275.09.07/kernel/nv-chrdev.o /tmp/selfgz2557/NVIDIA-Linu
   x-x86_64-275.09.07/kernel/nv-mlock.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275
   .09.07/kernel/nv-procfs.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kern
   el/nv-usermap.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv_gvi.
   o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-vm.o /tmp/selfgz25
   57/NVIDIA-Linux-x86_64-275.09.07/kernel/os-agp.o /tmp/selfgz2557/NVIDIA-Linu
   x-x86_64-275.09.07/kernel/os-interface.o /tmp/selfgz2557/NVIDIA-Linux-x86_64
   -275.09.07/kernel/os-smp.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/ker
   nel/os-usermap.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/os-reg
   istry.o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-cray.o /tmp/
   selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nv-i2c.o /tmp/selfgz2557/NVI
   DIA-Linux-x86_64-275.09.07/kernel/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/
   kernel/nvidia.ko;) > /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/mo
   dules.order
   make -f /usr/src/linux-headers-2.6.38-8-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.38-8-generic/Modul
   e.symvers -I /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/Module.sym
   vers  -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/Module.symvers
   -S -w  -s
   WARNING: could not find /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel
   /.nv-kernel.o.cmd for /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   v-kernel.o
     cc -Wp,-MD,/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/.nvidia.mo
   d.o.d  -nostdinc -isystem /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5
   .2/include  -I/usr/src/linux-headers-2.6.38-8-generic/arch/x86/include -Iinc
   lude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration 
   -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic
   -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -f
   stack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS
   _CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchron
   ous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than
   =1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-
   after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC
   _HAVE_ASM_GOTO -I/tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel -Wall 
   -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -D
   NV_VERSION_STRING=\"275.09.07\" -Wno-unused-function -mno-red-zone -mcmodel=
   kernel -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KB
   UILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE  -c -o
   /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nvidia.mod.o /tmp/selfg
   z2557/NVIDIA-Linux-x86_64-275.09.0
   7/kernel/nvidia.mod.c
   In file included from include/linux/kernel.h:17:0,
                    from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/percpu.h:44,
                    from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.38-8-generic/arch/x86/inclu
   de/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:7,
                    from include/linux/module.h:9,
                    from /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/n
   vidia.mod.c:1:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:41: warning: signed and unsigned type in condition
   al expression
     ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.38-8-generic/scripts/mod
   ule-common.lds --build-id  -o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/
   kernel/nvidia.ko /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/kernel/nvidia
   .o /tmp/selfgz2557/NVIDIA-Linux-x86_64-275.09.07/k
   ernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [  179.808043] cfg80211: Updating information on frequency 2462 MHz for a 20
   MHz width channel with regulatory rule:
   [  179.808046] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000
   mBm)
   [  179.808048] cfg80211: Updating information on frequency 2467 MHz for a 20
   MHz width channel with regulatory rule:
   [  179.808051] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000
   mBm)
   [  179.808053] cfg80211: Updating information on frequency 2472 MHz for a 20
   MHz width channel with regulatory rule:
   [  179.808056] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000
   mBm)
   [  179.808059] cfg80211: Updating information on frequency 2484 MHz for a 20
   MHz width channel with regulatory rule:
   [  179.808062] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000
   mBm)
   [  179.808065] cfg80211: World regulatory domain updated:
   [  179.808066] cfg80211:     (start_freq - end_freq @ bandwidth),
   (max_antenna_gain, max_eirp)
   [  179.808069] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300
   mBi, 2000 mBm)
   [  179.808072] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300
   mBi, 2000 mBm)
   [  179.808075] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300
   mBi, 2000 mBm)
   [  179.808078] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300
   mBi, 2000 mBm)
   [  179.808080] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300
   mBi, 2000 mBm)
   [  221.130901] usb 8-2: USB disconnect, address 2
   [  222.698473] usb 8-2: new low speed USB device using uhci_hcd and address
   3
   [  222.962296] input: Genius Optical Mouse as
   /devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input7
   [  222.962465] generic-usb 0003:0458:003A.0004: input,hidraw0: USB HID v1.11
   Mouse [Genius Optical Mouse] on usb-0000:00:1d.2-2/input0
   [  248.751024] nvidia 0000:03:00.0: PCI INT A disabled
   [  272.943147] nvidia 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ
   16
   [  272.943154] nvidia 0000:03:00.0: setting latency timer to 64
   [  272.943157] vgaarb: device changed decodes:
   PCI:0000:03:00.0,olddecodes=none,decodes=none:owns=io+mem
   [  272.943321] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  275.09.07 
   Wed Jun  8 14:16:46 PDT 2011
   [  272.946661] nvidia 0000:03:00.0: PCI INT A disabled
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: Yes)
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64'
   (275.09.07):
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
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 275.09.07)
   is now complete.

```

xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 275.09.07  (buildmeister@swio-display-x86-rhel47-03.nvidia.com)  Wed Jun  8 14:38:32 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Don't have an xorg.0.log file

And finally .xsession-errors

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_NZ.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-GdHIs2
GNOME_KEYRING_PID=1911
GNOME_KEYRING_CONTROL=/tmp/keyring-GdHIs2
SSH_AUTH_SOCK=/tmp/keyring-GdHIs2/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-GdHIs2
SSH_AUTH_SOCK=/tmp/keyring-GdHIs2/ssh
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing gnomecompat options...done
Initializing place options...done
Initializing mousepoll options...done
Initializing animation options...done
Initializing workarounds options...done
Initializing vpswitch options...done
Initializing wall options...done
I/O warning : failed to load external entity "/home/terry/.compiz/session/10317c746cfd6b8c08131033929277272800000018610032"
Initializing session options...done
Initializing grid options...done
Initializing resize options...done
Initializing move options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing staticswitcher options...done
Initializing fade options...done
Initializing scale options...done
Starting unity-window-decorator
** (nm-applet:1962): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1962): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1962): DEBUG: old state indicates that this was not a disconnect 0
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
Initializing nautilus-gdu extension
Exception in thread Fetcher:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 505, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/bin/indicator-weather", line 1148, in get_new_weather_data
    weather = self.get_weather()
  File "/usr/bin/indicator-weather", line 1210, in get_weather
    self.current_location.update_weather_data(self.weather_source)
  File "/usr/bin/indicator-weather", line 329, in update_weather_data
    self.weather = Weather(self.location_details['yahoo id'], source, self.metric_system, self.wind_unit, self.location_details['latitude'], self.location_details['longitude'])
  File "/usr/bin/indicator-weather", line 518, in __init__
    self.__report = pywapi.get_weather_from_yahoo (location_id, 'imperial')
  File "/usr/lib/pymodules/python2.7/pywapi.py", line 192, in get_weather_from_yahoo
    handler = urllib2.urlopen(url)
  File "/usr/lib/python2.7/urllib2.py", line 126, in urlopen
    return _opener.open(url, data, timeout)
  File "/usr/lib/python2.7/urllib2.py", line 391, in open
    response = self._open(req, data)
  File "/usr/lib/python2.7/urllib2.py", line 409, in _open
    '_open', req)
  File "/usr/lib/python2.7/urllib2.py", line 369, in _call_chain
    result = func(*args)
  File "/usr/lib/python2.7/urllib2.py", line 1185, in http_open
    return self.do_open(httplib.HTTPConnection, req)
  File "/usr/lib/python2.7/urllib2.py", line 1160, in do_open
    raise URLError(err)
URLError: <urlopen error [Errno -2] Name or service not known>

** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 3 events

(nautilus:1942): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: info_fn: file /var/lib/samba/usershares/photos is not a well formed usershare file.
info_fn: Error was Path not allowed.


** (gnome-screensaver:2197): WARNING **: screensaver already running in this session
** (nm-applet:1962): DEBUG: foo_client_state_changed_cb
** (nm-applet:1962): DEBUG: foo_client_state_changed_cb
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (deja-dup-monitor:1953): DEBUG: monitor.vala:263: Invalid next run date.  Not scheduling a backup.
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
/tmp/thunderbird.tbindicator.default-fifo204
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Wrapper *** ERROR: no valid NPP -> PluginInstance mapping found
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
Created new window in existing browser session.
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
gvfs-open: httphttp://www.boppoly.ac.nz/go/programmes/school-of-applied-technology/bridging-programmes/mathematics-bridging-programme-l4: error opening location: The specified location is not supported
gvfs-open: httphttp://www.boppoly.ac.nz/go/programmes/school-of-applied-technology/bridging-programmes/mathematics-bridging-programme-l4: error opening location: The specified location is not supported

(evolution-alarm-notify:1950): evolution-alarm-notify-WARNING **: alarm.c:253: Requested removal of nonexistent alarm!
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1943): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

```

Cheers

---

### Post by MAFoElffen on 2011-07-10
> **terrykiwi83 said:**
> Am assuming you want me to post these from within 2.6.38 as I can't access 2.6.39?

Don't have an xorg.0.log file

You do... My fualt on sysntax.  Should have been:

/var/log/Xorg.0.log

But Let me explain first.  The logfile filename follows thiese conventions- Xorg.n.log... where the variable "n" is 0 through 5... Then it goes the same but appends a .old to the end of the filename.  So it keeps the logs of the current seesion and 11 sessions back.  

The reason I took the time to explain this, We need to look for the log of a session where it failed.  For example, if you booted up on the new kernel (2.6.39.x), let bork... Then booted up on the earlier kernel... Then the log file would be "Xorg.1.log"

Next questions on the kernel- Did you get from the kernel mainline PPA?  Stil waiting on the last info that I added after an edit... You probly didn't see if while you where busy responding.

I don't see anything glaring out at me from the info you returned, but I'm rereading it.

---

### Post by terrykiwi83 on 2011-07-10
Here is whats in my Xorg.0.log

```

[    14.876] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.876] X Protocol Version 11, Revision 0
[    14.876] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.876] Current Operating System: Linux COMMODORE 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    14.876] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro quiet splash vt.handoff=7
[    14.876] Build Date: 21 May 2011  11:48:41AM
[    14.876] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.876] Current version of pixman: 0.20.2
[    14.876] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.876] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.876] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 11 11:07:59 2011
[    14.876] (==) Using config file: "/etc/X11/xorg.conf"
[    14.876] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.876] (==) ServerLayout "Layout0"
[    14.876] (**) |-->Screen "Screen0" (0)
[    14.876] (**) |   |-->Monitor "Monitor0"
[    14.876] (**) |   |-->Device "Device0"
[    14.876] (**) |-->Input Device "Keyboard0"
[    14.876] (**) |-->Input Device "Mouse0"
[    14.877] (==) Automatically adding devices
[    14.877] (==) Automatically enabling devices
[    14.877] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.877] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.877] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.877] (WW) Disabling Keyboard0
[    14.877] (WW) Disabling Mouse0
[    14.877] (II) Loader magic: 0x7e0280
[    14.877] (II) Module ABI versions:
[    14.877] 	X.Org ANSI C Emulation: 0.4
[    14.877] 	X.Org Video Driver: 10.0
[    14.877] 	X.Org XInput driver : 12.3
[    14.877] 	X.Org Server Extension : 5.0
[    14.878] (--) PCI:*(0:3:0:0) 10de:06cd:1043:8347 rev 163, Mem @ 0xf6000000/33554432, 0xe0000000/134217728, 0xec000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    14.878] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.878] (II) LoadModule: "extmod"
[    14.879] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.880] (II) Module extmod: vendor="X.Org Foundation"
[    14.880] 	compiled for 1.10.1, module version = 1.0.0
[    14.880] 	Module class: X.Org Server Extension
[    14.880] 	ABI class: X.Org Server Extension, version 5.0
[    14.880] (II) Loading extension MIT-SCREEN-SAVER
[    14.880] (II) Loading extension XFree86-VidModeExtension
[    14.880] (II) Loading extension XFree86-DGA
[    14.880] (II) Loading extension DPMS
[    14.880] (II) Loading extension XVideo
[    14.880] (II) Loading extension XVideo-MotionCompensation
[    14.880] (II) Loading extension X-Resource
[    14.880] (II) LoadModule: "dbe"
[    14.880] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.880] (II) Module dbe: vendor="X.Org Foundation"
[    14.880] 	compiled for 1.10.1, module version = 1.0.0
[    14.880] 	Module class: X.Org Server Extension
[    14.880] 	ABI class: X.Org Server Extension, version 5.0
[    14.880] (II) Loading extension DOUBLE-BUFFER
[    14.880] (II) LoadModule: "glx"
[    14.880] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.886] (II) Module glx: vendor="NVIDIA Corporation"
[    14.886] 	compiled for 4.0.2, module version = 1.0.0
[    14.886] 	Module class: X.Org Server Extension
[    14.886] (II) NVIDIA GLX Module  275.09.07  Wed Jun  8 14:34:43 PDT 2011
[    14.886] (II) Loading extension GLX
[    14.886] (II) LoadModule: "record"
[    14.887] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.887] (II) Module record: vendor="X.Org Foundation"
[    14.887] 	compiled for 1.10.1, module version = 1.13.0
[    14.887] 	Module class: X.Org Server Extension
[    14.887] 	ABI class: X.Org Server Extension, version 5.0
[    14.887] (II) Loading extension RECORD
[    14.887] (II) LoadModule: "dri"
[    14.887] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.887] (II) Module dri: vendor="X.Org Foundation"
[    14.887] 	compiled for 1.10.1, module version = 1.0.0
[    14.887] 	ABI class: X.Org Server Extension, version 5.0
[    14.887] (II) Loading extension XFree86-DRI
[    14.887] (II) LoadModule: "dri2"
[    14.887] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.887] (II) Module dri2: vendor="X.Org Foundation"
[    14.887] 	compiled for 1.10.1, module version = 1.2.0
[    14.887] 	ABI class: X.Org Server Extension, version 5.0
[    14.887] (II) Loading extension DRI2
[    14.887] (II) LoadModule: "nvidia"
[    14.887] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.888] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.888] 	compiled for 4.0.2, module version = 1.0.0
[    14.888] 	Module class: X.Org Video Driver
[    14.888] (II) NVIDIA dlloader X Driver  275.09.07  Wed Jun  8 14:18:12 PDT 2011
[    14.888] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.888] (++) using VT number 7

[    14.888] (II) Loading sub module "fb"
[    14.888] (II) LoadModule: "fb"
[    14.888] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.888] (II) Module fb: vendor="X.Org Foundation"
[    14.888] 	compiled for 1.10.1, module version = 1.0.0
[    14.888] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.888] (II) Loading sub module "wfb"
[    14.888] (II) LoadModule: "wfb"
[    14.888] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.888] (II) Module wfb: vendor="X.Org Foundation"
[    14.888] 	compiled for 1.10.1, module version = 1.0.0
[    14.888] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.888] (II) Loading sub module "ramdac"
[    14.888] (II) LoadModule: "ramdac"
[    14.888] (II) Module "ramdac" already built-in
[    14.888] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.888] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.888] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.889] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.889] (==) NVIDIA(0): RGB weight 888
[    14.889] (==) NVIDIA(0): Default visual is TrueColor
[    14.889] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.649] (II) NVIDIA(GPU-0): Display (AOC 2243W (DFP-0)) does not support NVIDIA 3D Vision
[    15.649] (II) NVIDIA(GPU-0):     stereo.
[    15.682] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2))
[    15.682] (II) NVIDIA(GPU-0):     does not support NVIDIA 3D Vision stereo.
[    15.684] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 470 (GF100) at PCI:3:0:0 (GPU-0)
[    15.684] (--) NVIDIA(0): Memory: 1310720 kBytes
[    15.684] (--) NVIDIA(0): VideoBIOS: 70.00.1a.00.03
[    15.684] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    15.684] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    15.684] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 470 at PCI:3:0:0
[    15.684] (--) NVIDIA(0):     AOC 2243W (DFP-0)
[    15.684] (--) NVIDIA(0):     Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2)
[    15.684] (--) NVIDIA(0): AOC 2243W (DFP-0): 330.0 MHz maximum pixel clock
[    15.684] (--) NVIDIA(0): AOC 2243W (DFP-0): Internal Dual Link TMDS
[    15.684] (--) NVIDIA(0): Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2): 330.0 MHz
[    15.684] (--) NVIDIA(0):     maximum pixel clock
[    15.684] (--) NVIDIA(0): Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2): Internal
[    15.684] (--) NVIDIA(0):     Dual Link TMDS
[    15.751] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    15.751] (==) NVIDIA(0): 
[    15.751] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    15.751] (==) NVIDIA(0):     will be used as the requested mode.
[    15.751] (==) NVIDIA(0): 
[    15.751] (II) NVIDIA(0): Validated modes:
[    15.751] (II) NVIDIA(0):     "nvidia-auto-select"
[    15.751] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    15.778] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[    15.778] (--) NVIDIA(0):     option
[    15.778] (--) Depth 24 pixmap format is 32 bpp
[    15.778] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    15.778] (II) NVIDIA:     access.
[    15.783] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[    15.783] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[    15.783] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[    15.783] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[    15.783] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[    15.783] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[    15.783] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[    15.783] (II) NVIDIA(0):     Config Options in the README.
[    15.785] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    15.852] (II) Loading extension NV-GLX
[    15.914] (==) NVIDIA(0): Disabling shared memory pixmaps
[    15.914] (==) NVIDIA(0): Backing store disabled
[    15.914] (==) NVIDIA(0): Silken mouse enabled
[    15.914] (**) NVIDIA(0): DPMS enabled
[    15.914] (II) Loading extension NV-CONTROL
[    15.914] (II) Loading extension XINERAMA
[    15.914] (II) Loading sub module "dri2"
[    15.914] (II) LoadModule: "dri2"
[    15.915] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.915] (II) Module dri2: vendor="X.Org Foundation"
[    15.915] 	compiled for 1.10.1, module version = 1.2.0
[    15.915] 	ABI class: X.Org Server Extension, version 5.0
[    15.915] (II) NVIDIA(0): [DRI2] Setup complete
[    15.915] (==) RandR enabled
[    15.915] (II) Initializing built-in extension Generic Event Extension
[    15.915] (II) Initializing built-in extension SHAPE
[    15.915] (II) Initializing built-in extension MIT-SHM
[    15.915] (II) Initializing built-in extension XInputExtension
[    15.915] (II) Initializing built-in extension XTEST
[    15.915] (II) Initializing built-in extension BIG-REQUESTS
[    15.915] (II) Initializing built-in extension SYNC
[    15.915] (II) Initializing built-in extension XKEYBOARD
[    15.915] (II) Initializing built-in extension XC-MISC
[    15.915] (II) Initializing built-in extension SECURITY
[    15.915] (II) Initializing built-in extension XINERAMA
[    15.915] (II) Initializing built-in extension XFIXES
[    15.915] (II) Initializing built-in extension RENDER
[    15.915] (II) Initializing built-in extension RANDR
[    15.915] (II) Initializing built-in extension COMPOSITE
[    15.915] (II) Initializing built-in extension DAMAGE
[    15.915] (II) Initializing built-in extension GESTURE
[    15.916] (II) Initializing extension GLX
[    15.932] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.939] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.939] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.939] (II) LoadModule: "evdev"
[    15.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.939] (II) Module evdev: vendor="X.Org Foundation"
[    15.939] 	compiled for 1.10.0.902, module version = 2.6.0
[    15.939] 	Module class: X.Org XInput Driver
[    15.939] 	ABI class: X.Org XInput driver, version 12.3
[    15.939] (II) Using input driver 'evdev' for 'Power Button'
[    15.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.940] (**) Power Button: always reports core events
[    15.940] (**) Power Button: Device: "/dev/input/event1"
[    16.020] (--) Power Button: Found keys
[    16.020] (II) Power Button: Configuring as keyboard
[    16.020] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.020] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.020] (**) Option "xkb_rules" "evdev"
[    16.020] (**) Option "xkb_model" "pc105"
[    16.020] (**) Option "xkb_layout" "us"
[    16.022] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.022] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.022] (II) Using input driver 'evdev' for 'Power Button'
[    16.022] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.022] (**) Power Button: always reports core events
[    16.022] (**) Power Button: Device: "/dev/input/event0"
[    16.070] (--) Power Button: Found keys
[    16.070] (II) Power Button: Configuring as keyboard
[    16.070] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.070] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.070] (**) Option "xkb_rules" "evdev"
[    16.070] (**) Option "xkb_model" "pc105"
[    16.070] (**) Option "xkb_layout" "us"
[    16.073] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    16.073] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.073] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    16.073] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.073] (**) Logitech USB Receiver: always reports core events
[    16.073] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    16.120] (--) Logitech USB Receiver: Found keys
[    16.120] (II) Logitech USB Receiver: Configuring as keyboard
[    16.120] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2/event2"
[    16.120] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.120] (**) Option "xkb_rules" "evdev"
[    16.120] (**) Option "xkb_model" "pc105"
[    16.120] (**) Option "xkb_layout" "us"
[    16.120] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    16.120] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.120] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.120] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    16.120] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.120] (**) Logitech USB Receiver: always reports core events
[    16.120] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    16.170] (--) Logitech USB Receiver: Found 12 mouse buttons
[    16.170] (--) Logitech USB Receiver: Found scroll wheel(s)
[    16.170] (--) Logitech USB Receiver: Found relative axes
[    16.170] (--) Logitech USB Receiver: Found x and y relative axes
[    16.170] (--) Logitech USB Receiver: Found absolute axes
[    16.170] (II) evdev-grail: failed to open grail, no gesture support
[    16.170] (--) Logitech USB Receiver: Found keys
[    16.170] (II) Logitech USB Receiver: Configuring as mouse
[    16.170] (II) Logitech USB Receiver: Configuring as keyboard
[    16.170] (II) Logitech USB Receiver: Adding scrollwheel support
[    16.170] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.170] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.170] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input3/event3"
[    16.170] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.170] (**) Option "xkb_rules" "evdev"
[    16.170] (**) Option "xkb_model" "pc105"
[    16.170] (**) Option "xkb_layout" "us"
[    16.170] (II) Logitech USB Receiver: initialized for relative axes.
[    16.170] (WW) Logitech USB Receiver: ignoring absolute axes.
[    16.170] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    16.170] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    16.170] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    16.170] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    16.170] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    16.170] (II) No input driver/identifier specified (ignoring)
[    16.171] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event6)
[    16.171] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    16.171] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
[    16.171] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.171] (**) USB 2.0 Camera: always reports core events
[    16.171] (**) USB 2.0 Camera: Device: "/dev/input/event6"
[    16.220] (--) USB 2.0 Camera: Found keys
[    16.220] (II) USB 2.0 Camera: Configuring as keyboard
[    16.220] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input6/event6"
[    16.220] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD)
[    16.220] (**) Option "xkb_rules" "evdev"
[    16.220] (**) Option "xkb_model" "pc105"
[    16.220] (**) Option "xkb_layout" "us"
[    16.221] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event5)
[    16.221] (II) No input driver/identifier specified (ignoring)
[    16.223] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
[    16.223] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[    16.223] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[    16.223] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.223] (**) Genius Optical Mouse: always reports core events
[    16.223] (**) Genius Optical Mouse: Device: "/dev/input/event4"
[    16.300] (--) Genius Optical Mouse: Found 3 mouse buttons
[    16.300] (--) Genius Optical Mouse: Found scroll wheel(s)
[    16.300] (--) Genius Optical Mouse: Found relative axes
[    16.300] (--) Genius Optical Mouse: Found x and y relative axes
[    16.300] (II) Genius Optical Mouse: Configuring as mouse
[    16.300] (II) Genius Optical Mouse: Adding scrollwheel support
[    16.300] (**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[    16.300] (**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.300] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input4/event4"
[    16.300] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
[    16.300] (II) Genius Optical Mouse: initialized for relative axes.
[    16.300] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[    16.300] (**) Genius Optical Mouse: (accel) acceleration profile 0
[    16.300] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[    16.300] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[    16.300] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse1)
[    16.300] (II) No input driver/identifier specified (ignoring)
[   154.253] (II) NVIDIA(0): Setting mode
[   154.253] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select@1920x1080+0+0,DFP-2:nvidia-auto-select@1280x1024+1920+0"

```

Xorg.1.log

```

[    14.831] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.831] X Protocol Version 11, Revision 0
[    14.831] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.831] Current Operating System: Linux COMMODORE 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 14:19:01 UTC 2011 x86_64
[    14.831] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro quiet splash vt.handoff=7
[    14.831] Build Date: 21 May 2011  11:48:41AM
[    14.831] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.831] Current version of pixman: 0.20.2
[    14.831] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.831] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.831] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Jul 11 11:06:15 2011
[    14.831] (==) Using config file: "/etc/X11/xorg.conf"
[    14.831] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.832] (==) ServerLayout "Layout0"
[    14.832] (**) |-->Screen "Screen0" (0)
[    14.832] (**) |   |-->Monitor "Monitor0"
[    14.832] (**) |   |-->Device "Device0"
[    14.832] (**) |-->Input Device "Keyboard0"
[    14.832] (**) |-->Input Device "Mouse0"
[    14.832] (==) Automatically adding devices
[    14.832] (==) Automatically enabling devices
[    14.832] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.832] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.832] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.832] (WW) Disabling Keyboard0
[    14.832] (WW) Disabling Mouse0
[    14.832] (II) Loader magic: 0x7e0280
[    14.832] (II) Module ABI versions:
[    14.832] 	X.Org ANSI C Emulation: 0.4
[    14.832] 	X.Org Video Driver: 10.0
[    14.832] 	X.Org XInput driver : 12.3
[    14.832] 	X.Org Server Extension : 5.0
[    14.833] (--) PCI:*(0:3:0:0) 10de:06cd:1043:8347 rev 163, Mem @ 0xf6000000/33554432, 0xe0000000/134217728, 0xec000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    14.833] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.833] (II) LoadModule: "extmod"
[    14.833] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.833] (II) Module extmod: vendor="X.Org Foundation"
[    14.833] 	compiled for 1.10.1, module version = 1.0.0
[    14.833] 	Module class: X.Org Server Extension
[    14.833] 	ABI class: X.Org Server Extension, version 5.0
[    14.833] (II) Loading extension MIT-SCREEN-SAVER
[    14.833] (II) Loading extension XFree86-VidModeExtension
[    14.833] (II) Loading extension XFree86-DGA
[    14.833] (II) Loading extension DPMS
[    14.833] (II) Loading extension XVideo
[    14.833] (II) Loading extension XVideo-MotionCompensation
[    14.833] (II) Loading extension X-Resource
[    14.833] (II) LoadModule: "dbe"
[    14.833] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.834] (II) Module dbe: vendor="X.Org Foundation"
[    14.834] 	compiled for 1.10.1, module version = 1.0.0
[    14.834] 	Module class: X.Org Server Extension
[    14.834] 	ABI class: X.Org Server Extension, version 5.0
[    14.834] (II) Loading extension DOUBLE-BUFFER
[    14.834] (II) LoadModule: "glx"
[    14.834] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.841] (II) Module glx: vendor="NVIDIA Corporation"
[    14.841] 	compiled for 4.0.2, module version = 1.0.0
[    14.841] 	Module class: X.Org Server Extension
[    14.842] (II) NVIDIA GLX Module  275.09.07  Wed Jun  8 14:34:43 PDT 2011
[    14.842] (II) Loading extension GLX
[    14.842] (II) LoadModule: "record"
[    14.842] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.842] (II) Module record: vendor="X.Org Foundation"
[    14.842] 	compiled for 1.10.1, module version = 1.13.0
[    14.842] 	Module class: X.Org Server Extension
[    14.842] 	ABI class: X.Org Server Extension, version 5.0
[    14.842] (II) Loading extension RECORD
[    14.842] (II) LoadModule: "dri"
[    14.842] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.842] (II) Module dri: vendor="X.Org Foundation"
[    14.842] 	compiled for 1.10.1, module version = 1.0.0
[    14.842] 	ABI class: X.Org Server Extension, version 5.0
[    14.842] (II) Loading extension XFree86-DRI
[    14.842] (II) LoadModule: "dri2"
[    14.842] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.842] (II) Module dri2: vendor="X.Org Foundation"
[    14.842] 	compiled for 1.10.1, module version = 1.2.0
[    14.842] 	ABI class: X.Org Server Extension, version 5.0
[    14.843] (II) Loading extension DRI2
[    14.843] (II) LoadModule: "nvidia"
[    14.843] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.843] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.843] 	compiled for 4.0.2, module version = 1.0.0
[    14.843] 	Module class: X.Org Video Driver
[    14.843] (II) NVIDIA dlloader X Driver  275.09.07  Wed Jun  8 14:18:12 PDT 2011
[    14.843] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.843] (--) using VT number 2

[    14.844] (II) Loading sub module "fb"
[    14.844] (II) LoadModule: "fb"
[    14.844] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.844] (II) Module fb: vendor="X.Org Foundation"
[    14.844] 	compiled for 1.10.1, module version = 1.0.0
[    14.844] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.844] (II) Loading sub module "wfb"
[    14.844] (II) LoadModule: "wfb"
[    14.844] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.844] (II) Module wfb: vendor="X.Org Foundation"
[    14.844] 	compiled for 1.10.1, module version = 1.0.0
[    14.844] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.844] (II) Loading sub module "ramdac"
[    14.844] (II) LoadModule: "ramdac"
[    14.844] (II) Module "ramdac" already built-in
[    14.844] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.844] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.844] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.844] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.844] (==) NVIDIA(0): RGB weight 888
[    14.844] (==) NVIDIA(0): Default visual is TrueColor
[    14.844] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.845] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    14.845] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    14.845] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    14.845] (EE) NVIDIA(0):  *** Aborting ***
[    14.845] (II) UnloadModule: "nvidia"
[    14.845] (II) Unloading nvidia
[    14.845] (II) UnloadModule: "wfb"
[    14.845] (II) Unloading wfb
[    14.845] (II) UnloadModule: "fb"
[    14.845] (II) Unloading fb
[    14.845] (EE) Screen(s) found, but none have a usable configuration.
[    14.845] 
Fatal server error:
[    14.845] no screens found
[    14.845] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    14.845] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    14.845] 
[    14.845]  ddxSigGiveUp: Closing log

```

Xorg.2.log

```

[    14.858] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.858] X Protocol Version 11, Revision 0
[    14.858] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.858] Current Operating System: Linux COMMODORE 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 14:19:01 UTC 2011 x86_64
[    14.858] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro quiet splash vt.handoff=7
[    14.858] Build Date: 21 May 2011  11:48:41AM
[    14.858] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.858] Current version of pixman: 0.20.2
[    14.858] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.858] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.858] (==) Log file: "/var/log/Xorg.2.log", Time: Mon Jul 11 11:06:15 2011
[    14.858] (==) Using config file: "/etc/X11/xorg.conf"
[    14.858] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.858] (==) ServerLayout "Layout0"
[    14.858] (**) |-->Screen "Screen0" (0)
[    14.858] (**) |   |-->Monitor "Monitor0"
[    14.858] (**) |   |-->Device "Device0"
[    14.858] (**) |-->Input Device "Keyboard0"
[    14.858] (**) |-->Input Device "Mouse0"
[    14.858] (==) Automatically adding devices
[    14.858] (==) Automatically enabling devices
[    14.858] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.858] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.858] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.858] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.859] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.859] 	Entry deleted from font path.
[    14.859] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.859] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.859] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.859] (WW) Disabling Keyboard0
[    14.859] (WW) Disabling Mouse0
[    14.859] (II) Loader magic: 0x7e0280
[    14.859] (II) Module ABI versions:
[    14.859] 	X.Org ANSI C Emulation: 0.4
[    14.859] 	X.Org Video Driver: 10.0
[    14.859] 	X.Org XInput driver : 12.3
[    14.859] 	X.Org Server Extension : 5.0
[    14.860] (--) PCI:*(0:3:0:0) 10de:06cd:1043:8347 rev 163, Mem @ 0xf6000000/33554432, 0xe0000000/134217728, 0xec000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    14.860] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.860] (II) LoadModule: "extmod"
[    14.860] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.860] (II) Module extmod: vendor="X.Org Foundation"
[    14.860] 	compiled for 1.10.1, module version = 1.0.0
[    14.860] 	Module class: X.Org Server Extension
[    14.860] 	ABI class: X.Org Server Extension, version 5.0
[    14.860] (II) Loading extension MIT-SCREEN-SAVER
[    14.860] (II) Loading extension XFree86-VidModeExtension
[    14.860] (II) Loading extension XFree86-DGA
[    14.860] (II) Loading extension DPMS
[    14.860] (II) Loading extension XVideo
[    14.860] (II) Loading extension XVideo-MotionCompensation
[    14.860] (II) Loading extension X-Resource
[    14.860] (II) LoadModule: "dbe"
[    14.860] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.860] (II) Module dbe: vendor="X.Org Foundation"
[    14.860] 	compiled for 1.10.1, module version = 1.0.0
[    14.860] 	Module class: X.Org Server Extension
[    14.860] 	ABI class: X.Org Server Extension, version 5.0
[    14.860] (II) Loading extension DOUBLE-BUFFER
[    14.860] (II) LoadModule: "glx"
[    14.860] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.868] (II) Module glx: vendor="NVIDIA Corporation"
[    14.868] 	compiled for 4.0.2, module version = 1.0.0
[    14.868] 	Module class: X.Org Server Extension
[    14.868] (II) NVIDIA GLX Module  275.09.07  Wed Jun  8 14:34:43 PDT 2011
[    14.868] (II) Loading extension GLX
[    14.868] (II) LoadModule: "record"
[    14.868] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.868] (II) Module record: vendor="X.Org Foundation"
[    14.868] 	compiled for 1.10.1, module version = 1.13.0
[    14.868] 	Module class: X.Org Server Extension
[    14.868] 	ABI class: X.Org Server Extension, version 5.0
[    14.868] (II) Loading extension RECORD
[    14.868] (II) LoadModule: "dri"
[    14.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.868] (II) Module dri: vendor="X.Org Foundation"
[    14.868] 	compiled for 1.10.1, module version = 1.0.0
[    14.868] 	ABI class: X.Org Server Extension, version 5.0
[    14.868] (II) Loading extension XFree86-DRI
[    14.868] (II) LoadModule: "dri2"
[    14.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.868] (II) Module dri2: vendor="X.Org Foundation"
[    14.868] 	compiled for 1.10.1, module version = 1.2.0
[    14.868] 	ABI class: X.Org Server Extension, version 5.0
[    14.868] (II) Loading extension DRI2
[    14.868] (II) LoadModule: "nvidia"
[    14.869] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.869] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.869] 	compiled for 4.0.2, module version = 1.0.0
[    14.869] 	Module class: X.Org Video Driver
[    14.869] (II) NVIDIA dlloader X Driver  275.09.07  Wed Jun  8 14:18:12 PDT 2011
[    14.869] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.869] (--) using VT number 2

[    14.869] (II) Loading sub module "fb"
[    14.869] (II) LoadModule: "fb"
[    14.870] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.870] (II) Module fb: vendor="X.Org Foundation"
[    14.870] 	compiled for 1.10.1, module version = 1.0.0
[    14.870] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.870] (II) Loading sub module "wfb"
[    14.870] (II) LoadModule: "wfb"
[    14.870] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.870] (II) Module wfb: vendor="X.Org Foundation"
[    14.870] 	compiled for 1.10.1, module version = 1.0.0
[    14.870] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.870] (II) Loading sub module "ramdac"
[    14.870] (II) LoadModule: "ramdac"
[    14.870] (II) Module "ramdac" already built-in
[    14.870] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.870] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.870] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.870] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.870] (==) NVIDIA(0): RGB weight 888
[    14.870] (==) NVIDIA(0): Default visual is TrueColor
[    14.870] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.870] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    14.870] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    14.870] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    14.870] (EE) NVIDIA(0):  *** Aborting ***
[    14.870] (II) UnloadModule: "nvidia"
[    14.871] (II) Unloading nvidia
[    14.871] (II) UnloadModule: "wfb"
[    14.871] (II) Unloading wfb
[    14.871] (II) UnloadModule: "fb"
[    14.871] (II) Unloading fb
[    14.871] (EE) Screen(s) found, but none have a usable configuration.
[    14.871] 
Fatal server error:
[    14.871] no screens found
[    14.871] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    14.871] Please also check the log file at "/var/log/Xorg.2.log" for additional information.
[    14.871] 
[    14.871]  ddxSigGiveUp: Closing log

```

Hopefully thats enough.

I got the kernel image & headers from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)

I downloaded and installed the following (Filenames shortened below);

linux-image-2.6.39-rc4-amd64.deb
linux-headers-2.6.39-rc4-all.deb
linux-headers-2.6.39-rc4-amd64.deb

All installed through Software centre.

Thanks again

---

### Post by terrykiwi83 on 2011-07-10
Here is whats in my Xorg.0.log

```

[    14.876] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.876] X Protocol Version 11, Revision 0
[    14.876] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.876] Current Operating System: Linux COMMODORE 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[    14.876] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro quiet splash vt.handoff=7
[    14.876] Build Date: 21 May 2011  11:48:41AM
[    14.876] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.876] Current version of pixman: 0.20.2
[    14.876] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.876] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.876] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 11 11:07:59 2011
[    14.876] (==) Using config file: "/etc/X11/xorg.conf"
[    14.876] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.876] (==) ServerLayout "Layout0"
[    14.876] (**) |-->Screen "Screen0" (0)
[    14.876] (**) |   |-->Monitor "Monitor0"
[    14.876] (**) |   |-->Device "Device0"
[    14.876] (**) |-->Input Device "Keyboard0"
[    14.876] (**) |-->Input Device "Mouse0"
[    14.877] (==) Automatically adding devices
[    14.877] (==) Automatically enabling devices
[    14.877] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.877] 	Entry deleted from font path.
[    14.877] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.877] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.877] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.877] (WW) Disabling Keyboard0
[    14.877] (WW) Disabling Mouse0
[    14.877] (II) Loader magic: 0x7e0280
[    14.877] (II) Module ABI versions:
[    14.877] 	X.Org ANSI C Emulation: 0.4
[    14.877] 	X.Org Video Driver: 10.0
[    14.877] 	X.Org XInput driver : 12.3
[    14.877] 	X.Org Server Extension : 5.0
[    14.878] (--) PCI:*(0:3:0:0) 10de:06cd:1043:8347 rev 163, Mem @ 0xf6000000/33554432, 0xe0000000/134217728, 0xec000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    14.878] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.878] (II) LoadModule: "extmod"
[    14.879] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.880] (II) Module extmod: vendor="X.Org Foundation"
[    14.880] 	compiled for 1.10.1, module version = 1.0.0
[    14.880] 	Module class: X.Org Server Extension
[    14.880] 	ABI class: X.Org Server Extension, version 5.0
[    14.880] (II) Loading extension MIT-SCREEN-SAVER
[    14.880] (II) Loading extension XFree86-VidModeExtension
[    14.880] (II) Loading extension XFree86-DGA
[    14.880] (II) Loading extension DPMS
[    14.880] (II) Loading extension XVideo
[    14.880] (II) Loading extension XVideo-MotionCompensation
[    14.880] (II) Loading extension X-Resource
[    14.880] (II) LoadModule: "dbe"
[    14.880] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.880] (II) Module dbe: vendor="X.Org Foundation"
[    14.880] 	compiled for 1.10.1, module version = 1.0.0
[    14.880] 	Module class: X.Org Server Extension
[    14.880] 	ABI class: X.Org Server Extension, version 5.0
[    14.880] (II) Loading extension DOUBLE-BUFFER
[    14.880] (II) LoadModule: "glx"
[    14.880] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.886] (II) Module glx: vendor="NVIDIA Corporation"
[    14.886] 	compiled for 4.0.2, module version = 1.0.0
[    14.886] 	Module class: X.Org Server Extension
[    14.886] (II) NVIDIA GLX Module  275.09.07  Wed Jun  8 14:34:43 PDT 2011
[    14.886] (II) Loading extension GLX
[    14.886] (II) LoadModule: "record"
[    14.887] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.887] (II) Module record: vendor="X.Org Foundation"
[    14.887] 	compiled for 1.10.1, module version = 1.13.0
[    14.887] 	Module class: X.Org Server Extension
[    14.887] 	ABI class: X.Org Server Extension, version 5.0
[    14.887] (II) Loading extension RECORD
[    14.887] (II) LoadModule: "dri"
[    14.887] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.887] (II) Module dri: vendor="X.Org Foundation"
[    14.887] 	compiled for 1.10.1, module version = 1.0.0
[    14.887] 	ABI class: X.Org Server Extension, version 5.0
[    14.887] (II) Loading extension XFree86-DRI
[    14.887] (II) LoadModule: "dri2"
[    14.887] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.887] (II) Module dri2: vendor="X.Org Foundation"
[    14.887] 	compiled for 1.10.1, module version = 1.2.0
[    14.887] 	ABI class: X.Org Server Extension, version 5.0
[    14.887] (II) Loading extension DRI2
[    14.887] (II) LoadModule: "nvidia"
[    14.887] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.888] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.888] 	compiled for 4.0.2, module version = 1.0.0
[    14.888] 	Module class: X.Org Video Driver
[    14.888] (II) NVIDIA dlloader X Driver  275.09.07  Wed Jun  8 14:18:12 PDT 2011
[    14.888] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.888] (++) using VT number 7

[    14.888] (II) Loading sub module "fb"
[    14.888] (II) LoadModule: "fb"
[    14.888] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.888] (II) Module fb: vendor="X.Org Foundation"
[    14.888] 	compiled for 1.10.1, module version = 1.0.0
[    14.888] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.888] (II) Loading sub module "wfb"
[    14.888] (II) LoadModule: "wfb"
[    14.888] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.888] (II) Module wfb: vendor="X.Org Foundation"
[    14.888] 	compiled for 1.10.1, module version = 1.0.0
[    14.888] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.888] (II) Loading sub module "ramdac"
[    14.888] (II) LoadModule: "ramdac"
[    14.888] (II) Module "ramdac" already built-in
[    14.888] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.888] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.888] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.889] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.889] (==) NVIDIA(0): RGB weight 888
[    14.889] (==) NVIDIA(0): Default visual is TrueColor
[    14.889] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    15.649] (II) NVIDIA(GPU-0): Display (AOC 2243W (DFP-0)) does not support NVIDIA 3D Vision
[    15.649] (II) NVIDIA(GPU-0):     stereo.
[    15.682] (II) NVIDIA(GPU-0): Display (Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2))
[    15.682] (II) NVIDIA(GPU-0):     does not support NVIDIA 3D Vision stereo.
[    15.684] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 470 (GF100) at PCI:3:0:0 (GPU-0)
[    15.684] (--) NVIDIA(0): Memory: 1310720 kBytes
[    15.684] (--) NVIDIA(0): VideoBIOS: 70.00.1a.00.03
[    15.684] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    15.684] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    15.684] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 470 at PCI:3:0:0
[    15.684] (--) NVIDIA(0):     AOC 2243W (DFP-0)
[    15.684] (--) NVIDIA(0):     Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2)
[    15.684] (--) NVIDIA(0): AOC 2243W (DFP-0): 330.0 MHz maximum pixel clock
[    15.684] (--) NVIDIA(0): AOC 2243W (DFP-0): Internal Dual Link TMDS
[    15.684] (--) NVIDIA(0): Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2): 330.0 MHz
[    15.684] (--) NVIDIA(0):     maximum pixel clock
[    15.684] (--) NVIDIA(0): Chi Mei Optoelectronics corp. CMC 17" AD (DFP-2): Internal
[    15.684] (--) NVIDIA(0):     Dual Link TMDS
[    15.751] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    15.751] (==) NVIDIA(0): 
[    15.751] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    15.751] (==) NVIDIA(0):     will be used as the requested mode.
[    15.751] (==) NVIDIA(0): 
[    15.751] (II) NVIDIA(0): Validated modes:
[    15.751] (II) NVIDIA(0):     "nvidia-auto-select"
[    15.751] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    15.778] (--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
[    15.778] (--) NVIDIA(0):     option
[    15.778] (--) Depth 24 pixmap format is 32 bpp
[    15.778] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    15.778] (II) NVIDIA:     access.
[    15.783] (II) NVIDIA(0): ACPI: failed to connect to the ACPI event daemon; the daemon
[    15.783] (II) NVIDIA(0):     may not be running or the "AcpidSocketPath" X
[    15.783] (II) NVIDIA(0):     configuration option may not be set correctly.  When the
[    15.783] (II) NVIDIA(0):     ACPI event daemon is available, the NVIDIA X driver will
[    15.783] (II) NVIDIA(0):     try to use it to receive ACPI event notifications.  For
[    15.783] (II) NVIDIA(0):     details, please see the "ConnectToAcpid" and
[    15.783] (II) NVIDIA(0):     "AcpidSocketPath" X configuration options in Appendix B: X
[    15.783] (II) NVIDIA(0):     Config Options in the README.
[    15.785] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    15.852] (II) Loading extension NV-GLX
[    15.914] (==) NVIDIA(0): Disabling shared memory pixmaps
[    15.914] (==) NVIDIA(0): Backing store disabled
[    15.914] (==) NVIDIA(0): Silken mouse enabled
[    15.914] (**) NVIDIA(0): DPMS enabled
[    15.914] (II) Loading extension NV-CONTROL
[    15.914] (II) Loading extension XINERAMA
[    15.914] (II) Loading sub module "dri2"
[    15.914] (II) LoadModule: "dri2"
[    15.915] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    15.915] (II) Module dri2: vendor="X.Org Foundation"
[    15.915] 	compiled for 1.10.1, module version = 1.2.0
[    15.915] 	ABI class: X.Org Server Extension, version 5.0
[    15.915] (II) NVIDIA(0): [DRI2] Setup complete
[    15.915] (==) RandR enabled
[    15.915] (II) Initializing built-in extension Generic Event Extension
[    15.915] (II) Initializing built-in extension SHAPE
[    15.915] (II) Initializing built-in extension MIT-SHM
[    15.915] (II) Initializing built-in extension XInputExtension
[    15.915] (II) Initializing built-in extension XTEST
[    15.915] (II) Initializing built-in extension BIG-REQUESTS
[    15.915] (II) Initializing built-in extension SYNC
[    15.915] (II) Initializing built-in extension XKEYBOARD
[    15.915] (II) Initializing built-in extension XC-MISC
[    15.915] (II) Initializing built-in extension SECURITY
[    15.915] (II) Initializing built-in extension XINERAMA
[    15.915] (II) Initializing built-in extension XFIXES
[    15.915] (II) Initializing built-in extension RENDER
[    15.915] (II) Initializing built-in extension RANDR
[    15.915] (II) Initializing built-in extension COMPOSITE
[    15.915] (II) Initializing built-in extension DAMAGE
[    15.915] (II) Initializing built-in extension GESTURE
[    15.916] (II) Initializing extension GLX
[    15.932] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    15.939] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    15.939] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    15.939] (II) LoadModule: "evdev"
[    15.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.939] (II) Module evdev: vendor="X.Org Foundation"
[    15.939] 	compiled for 1.10.0.902, module version = 2.6.0
[    15.939] 	Module class: X.Org XInput Driver
[    15.939] 	ABI class: X.Org XInput driver, version 12.3
[    15.939] (II) Using input driver 'evdev' for 'Power Button'
[    15.939] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    15.940] (**) Power Button: always reports core events
[    15.940] (**) Power Button: Device: "/dev/input/event1"
[    16.020] (--) Power Button: Found keys
[    16.020] (II) Power Button: Configuring as keyboard
[    16.020] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    16.020] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.020] (**) Option "xkb_rules" "evdev"
[    16.020] (**) Option "xkb_model" "pc105"
[    16.020] (**) Option "xkb_layout" "us"
[    16.022] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    16.022] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    16.022] (II) Using input driver 'evdev' for 'Power Button'
[    16.022] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.022] (**) Power Button: always reports core events
[    16.022] (**) Power Button: Device: "/dev/input/event0"
[    16.070] (--) Power Button: Found keys
[    16.070] (II) Power Button: Configuring as keyboard
[    16.070] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    16.070] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    16.070] (**) Option "xkb_rules" "evdev"
[    16.070] (**) Option "xkb_model" "pc105"
[    16.070] (**) Option "xkb_layout" "us"
[    16.073] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event2)
[    16.073] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.073] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    16.073] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.073] (**) Logitech USB Receiver: always reports core events
[    16.073] (**) Logitech USB Receiver: Device: "/dev/input/event2"
[    16.120] (--) Logitech USB Receiver: Found keys
[    16.120] (II) Logitech USB Receiver: Configuring as keyboard
[    16.120] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input2/event2"
[    16.120] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.120] (**) Option "xkb_rules" "evdev"
[    16.120] (**) Option "xkb_model" "pc105"
[    16.120] (**) Option "xkb_layout" "us"
[    16.120] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    16.120] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    16.120] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    16.120] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    16.120] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.120] (**) Logitech USB Receiver: always reports core events
[    16.120] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    16.170] (--) Logitech USB Receiver: Found 12 mouse buttons
[    16.170] (--) Logitech USB Receiver: Found scroll wheel(s)
[    16.170] (--) Logitech USB Receiver: Found relative axes
[    16.170] (--) Logitech USB Receiver: Found x and y relative axes
[    16.170] (--) Logitech USB Receiver: Found absolute axes
[    16.170] (II) evdev-grail: failed to open grail, no gesture support
[    16.170] (--) Logitech USB Receiver: Found keys
[    16.170] (II) Logitech USB Receiver: Configuring as mouse
[    16.170] (II) Logitech USB Receiver: Configuring as keyboard
[    16.170] (II) Logitech USB Receiver: Adding scrollwheel support
[    16.170] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    16.170] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.170] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input3/event3"
[    16.170] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    16.170] (**) Option "xkb_rules" "evdev"
[    16.170] (**) Option "xkb_model" "pc105"
[    16.170] (**) Option "xkb_layout" "us"
[    16.170] (II) Logitech USB Receiver: initialized for relative axes.
[    16.170] (WW) Logitech USB Receiver: ignoring absolute axes.
[    16.170] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    16.170] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    16.170] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    16.170] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    16.170] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    16.170] (II) No input driver/identifier specified (ignoring)
[    16.171] (II) config/udev: Adding input device USB 2.0 Camera (/dev/input/event6)
[    16.171] (**) USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    16.171] (II) Using input driver 'evdev' for 'USB 2.0 Camera'
[    16.171] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.171] (**) USB 2.0 Camera: always reports core events
[    16.171] (**) USB 2.0 Camera: Device: "/dev/input/event6"
[    16.220] (--) USB 2.0 Camera: Found keys
[    16.220] (II) USB 2.0 Camera: Configuring as keyboard
[    16.220] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input6/event6"
[    16.220] (II) XINPUT: Adding extended input device "USB 2.0 Camera" (type: KEYBOARD)
[    16.220] (**) Option "xkb_rules" "evdev"
[    16.220] (**) Option "xkb_model" "pc105"
[    16.220] (**) Option "xkb_layout" "us"
[    16.221] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event5)
[    16.221] (II) No input driver/identifier specified (ignoring)
[    16.223] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
[    16.223] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[    16.223] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[    16.223] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    16.223] (**) Genius Optical Mouse: always reports core events
[    16.223] (**) Genius Optical Mouse: Device: "/dev/input/event4"
[    16.300] (--) Genius Optical Mouse: Found 3 mouse buttons
[    16.300] (--) Genius Optical Mouse: Found scroll wheel(s)
[    16.300] (--) Genius Optical Mouse: Found relative axes
[    16.300] (--) Genius Optical Mouse: Found x and y relative axes
[    16.300] (II) Genius Optical Mouse: Configuring as mouse
[    16.300] (II) Genius Optical Mouse: Adding scrollwheel support
[    16.300] (**) Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[    16.300] (**) Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    16.300] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/input/input4/event4"
[    16.300] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE)
[    16.300] (II) Genius Optical Mouse: initialized for relative axes.
[    16.300] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[    16.300] (**) Genius Optical Mouse: (accel) acceleration profile 0
[    16.300] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[    16.300] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[    16.300] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse1)
[    16.300] (II) No input driver/identifier specified (ignoring)
[   154.253] (II) NVIDIA(0): Setting mode
[   154.253] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select@1920x1080+0+0,DFP-2:nvidia-auto-select@1280x1024+1920+0"

```

Xorg.1.log

```

[    14.831] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.831] X Protocol Version 11, Revision 0
[    14.831] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.831] Current Operating System: Linux COMMODORE 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 14:19:01 UTC 2011 x86_64
[    14.831] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro quiet splash vt.handoff=7
[    14.831] Build Date: 21 May 2011  11:48:41AM
[    14.831] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.831] Current version of pixman: 0.20.2
[    14.831] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.831] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.831] (==) Log file: "/var/log/Xorg.1.log", Time: Mon Jul 11 11:06:15 2011
[    14.831] (==) Using config file: "/etc/X11/xorg.conf"
[    14.831] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.832] (==) ServerLayout "Layout0"
[    14.832] (**) |-->Screen "Screen0" (0)
[    14.832] (**) |   |-->Monitor "Monitor0"
[    14.832] (**) |   |-->Device "Device0"
[    14.832] (**) |-->Input Device "Keyboard0"
[    14.832] (**) |-->Input Device "Mouse0"
[    14.832] (==) Automatically adding devices
[    14.832] (==) Automatically enabling devices
[    14.832] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.832] 	Entry deleted from font path.
[    14.832] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.832] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.832] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.832] (WW) Disabling Keyboard0
[    14.832] (WW) Disabling Mouse0
[    14.832] (II) Loader magic: 0x7e0280
[    14.832] (II) Module ABI versions:
[    14.832] 	X.Org ANSI C Emulation: 0.4
[    14.832] 	X.Org Video Driver: 10.0
[    14.832] 	X.Org XInput driver : 12.3
[    14.832] 	X.Org Server Extension : 5.0
[    14.833] (--) PCI:*(0:3:0:0) 10de:06cd:1043:8347 rev 163, Mem @ 0xf6000000/33554432, 0xe0000000/134217728, 0xec000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    14.833] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.833] (II) LoadModule: "extmod"
[    14.833] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.833] (II) Module extmod: vendor="X.Org Foundation"
[    14.833] 	compiled for 1.10.1, module version = 1.0.0
[    14.833] 	Module class: X.Org Server Extension
[    14.833] 	ABI class: X.Org Server Extension, version 5.0
[    14.833] (II) Loading extension MIT-SCREEN-SAVER
[    14.833] (II) Loading extension XFree86-VidModeExtension
[    14.833] (II) Loading extension XFree86-DGA
[    14.833] (II) Loading extension DPMS
[    14.833] (II) Loading extension XVideo
[    14.833] (II) Loading extension XVideo-MotionCompensation
[    14.833] (II) Loading extension X-Resource
[    14.833] (II) LoadModule: "dbe"
[    14.833] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.834] (II) Module dbe: vendor="X.Org Foundation"
[    14.834] 	compiled for 1.10.1, module version = 1.0.0
[    14.834] 	Module class: X.Org Server Extension
[    14.834] 	ABI class: X.Org Server Extension, version 5.0
[    14.834] (II) Loading extension DOUBLE-BUFFER
[    14.834] (II) LoadModule: "glx"
[    14.834] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.841] (II) Module glx: vendor="NVIDIA Corporation"
[    14.841] 	compiled for 4.0.2, module version = 1.0.0
[    14.841] 	Module class: X.Org Server Extension
[    14.842] (II) NVIDIA GLX Module  275.09.07  Wed Jun  8 14:34:43 PDT 2011
[    14.842] (II) Loading extension GLX
[    14.842] (II) LoadModule: "record"
[    14.842] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.842] (II) Module record: vendor="X.Org Foundation"
[    14.842] 	compiled for 1.10.1, module version = 1.13.0
[    14.842] 	Module class: X.Org Server Extension
[    14.842] 	ABI class: X.Org Server Extension, version 5.0
[    14.842] (II) Loading extension RECORD
[    14.842] (II) LoadModule: "dri"
[    14.842] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.842] (II) Module dri: vendor="X.Org Foundation"
[    14.842] 	compiled for 1.10.1, module version = 1.0.0
[    14.842] 	ABI class: X.Org Server Extension, version 5.0
[    14.842] (II) Loading extension XFree86-DRI
[    14.842] (II) LoadModule: "dri2"
[    14.842] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.842] (II) Module dri2: vendor="X.Org Foundation"
[    14.842] 	compiled for 1.10.1, module version = 1.2.0
[    14.842] 	ABI class: X.Org Server Extension, version 5.0
[    14.843] (II) Loading extension DRI2
[    14.843] (II) LoadModule: "nvidia"
[    14.843] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.843] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.843] 	compiled for 4.0.2, module version = 1.0.0
[    14.843] 	Module class: X.Org Video Driver
[    14.843] (II) NVIDIA dlloader X Driver  275.09.07  Wed Jun  8 14:18:12 PDT 2011
[    14.843] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.843] (--) using VT number 2

[    14.844] (II) Loading sub module "fb"
[    14.844] (II) LoadModule: "fb"
[    14.844] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.844] (II) Module fb: vendor="X.Org Foundation"
[    14.844] 	compiled for 1.10.1, module version = 1.0.0
[    14.844] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.844] (II) Loading sub module "wfb"
[    14.844] (II) LoadModule: "wfb"
[    14.844] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.844] (II) Module wfb: vendor="X.Org Foundation"
[    14.844] 	compiled for 1.10.1, module version = 1.0.0
[    14.844] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.844] (II) Loading sub module "ramdac"
[    14.844] (II) LoadModule: "ramdac"
[    14.844] (II) Module "ramdac" already built-in
[    14.844] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.844] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.844] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.844] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.844] (==) NVIDIA(0): RGB weight 888
[    14.844] (==) NVIDIA(0): Default visual is TrueColor
[    14.844] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.845] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    14.845] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    14.845] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    14.845] (EE) NVIDIA(0):  *** Aborting ***
[    14.845] (II) UnloadModule: "nvidia"
[    14.845] (II) Unloading nvidia
[    14.845] (II) UnloadModule: "wfb"
[    14.845] (II) Unloading wfb
[    14.845] (II) UnloadModule: "fb"
[    14.845] (II) Unloading fb
[    14.845] (EE) Screen(s) found, but none have a usable configuration.
[    14.845] 
Fatal server error:
[    14.845] no screens found
[    14.845] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    14.845] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[    14.845] 
[    14.845]  ddxSigGiveUp: Closing log

```

Xorg.2.log

```

[    14.858] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    14.858] X Protocol Version 11, Revision 0
[    14.858] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    14.858] Current Operating System: Linux COMMODORE 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 14:19:01 UTC 2011 x86_64
[    14.858] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro quiet splash vt.handoff=7
[    14.858] Build Date: 21 May 2011  11:48:41AM
[    14.858] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[    14.858] Current version of pixman: 0.20.2
[    14.858] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    14.858] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    14.858] (==) Log file: "/var/log/Xorg.2.log", Time: Mon Jul 11 11:06:15 2011
[    14.858] (==) Using config file: "/etc/X11/xorg.conf"
[    14.858] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    14.858] (==) ServerLayout "Layout0"
[    14.858] (**) |-->Screen "Screen0" (0)
[    14.858] (**) |   |-->Monitor "Monitor0"
[    14.858] (**) |   |-->Device "Device0"
[    14.858] (**) |-->Input Device "Keyboard0"
[    14.858] (**) |-->Input Device "Mouse0"
[    14.858] (==) Automatically adding devices
[    14.858] (==) Automatically enabling devices
[    14.858] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.858] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.858] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.858] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    14.858] 	Entry deleted from font path.
[    14.859] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    14.859] 	Entry deleted from font path.
[    14.859] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    14.859] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    14.859] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    14.859] (WW) Disabling Keyboard0
[    14.859] (WW) Disabling Mouse0
[    14.859] (II) Loader magic: 0x7e0280
[    14.859] (II) Module ABI versions:
[    14.859] 	X.Org ANSI C Emulation: 0.4
[    14.859] 	X.Org Video Driver: 10.0
[    14.859] 	X.Org XInput driver : 12.3
[    14.859] 	X.Org Server Extension : 5.0
[    14.860] (--) PCI:*(0:3:0:0) 10de:06cd:1043:8347 rev 163, Mem @ 0xf6000000/33554432, 0xe0000000/134217728, 0xec000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[    14.860] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    14.860] (II) LoadModule: "extmod"
[    14.860] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    14.860] (II) Module extmod: vendor="X.Org Foundation"
[    14.860] 	compiled for 1.10.1, module version = 1.0.0
[    14.860] 	Module class: X.Org Server Extension
[    14.860] 	ABI class: X.Org Server Extension, version 5.0
[    14.860] (II) Loading extension MIT-SCREEN-SAVER
[    14.860] (II) Loading extension XFree86-VidModeExtension
[    14.860] (II) Loading extension XFree86-DGA
[    14.860] (II) Loading extension DPMS
[    14.860] (II) Loading extension XVideo
[    14.860] (II) Loading extension XVideo-MotionCompensation
[    14.860] (II) Loading extension X-Resource
[    14.860] (II) LoadModule: "dbe"
[    14.860] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    14.860] (II) Module dbe: vendor="X.Org Foundation"
[    14.860] 	compiled for 1.10.1, module version = 1.0.0
[    14.860] 	Module class: X.Org Server Extension
[    14.860] 	ABI class: X.Org Server Extension, version 5.0
[    14.860] (II) Loading extension DOUBLE-BUFFER
[    14.860] (II) LoadModule: "glx"
[    14.860] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    14.868] (II) Module glx: vendor="NVIDIA Corporation"
[    14.868] 	compiled for 4.0.2, module version = 1.0.0
[    14.868] 	Module class: X.Org Server Extension
[    14.868] (II) NVIDIA GLX Module  275.09.07  Wed Jun  8 14:34:43 PDT 2011
[    14.868] (II) Loading extension GLX
[    14.868] (II) LoadModule: "record"
[    14.868] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    14.868] (II) Module record: vendor="X.Org Foundation"
[    14.868] 	compiled for 1.10.1, module version = 1.13.0
[    14.868] 	Module class: X.Org Server Extension
[    14.868] 	ABI class: X.Org Server Extension, version 5.0
[    14.868] (II) Loading extension RECORD
[    14.868] (II) LoadModule: "dri"
[    14.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    14.868] (II) Module dri: vendor="X.Org Foundation"
[    14.868] 	compiled for 1.10.1, module version = 1.0.0
[    14.868] 	ABI class: X.Org Server Extension, version 5.0
[    14.868] (II) Loading extension XFree86-DRI
[    14.868] (II) LoadModule: "dri2"
[    14.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    14.868] (II) Module dri2: vendor="X.Org Foundation"
[    14.868] 	compiled for 1.10.1, module version = 1.2.0
[    14.868] 	ABI class: X.Org Server Extension, version 5.0
[    14.868] (II) Loading extension DRI2
[    14.868] (II) LoadModule: "nvidia"
[    14.869] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.869] (II) Module nvidia: vendor="NVIDIA Corporation"
[    14.869] 	compiled for 4.0.2, module version = 1.0.0
[    14.869] 	Module class: X.Org Video Driver
[    14.869] (II) NVIDIA dlloader X Driver  275.09.07  Wed Jun  8 14:18:12 PDT 2011
[    14.869] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    14.869] (--) using VT number 2

[    14.869] (II) Loading sub module "fb"
[    14.869] (II) LoadModule: "fb"
[    14.870] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.870] (II) Module fb: vendor="X.Org Foundation"
[    14.870] 	compiled for 1.10.1, module version = 1.0.0
[    14.870] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.870] (II) Loading sub module "wfb"
[    14.870] (II) LoadModule: "wfb"
[    14.870] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.870] (II) Module wfb: vendor="X.Org Foundation"
[    14.870] 	compiled for 1.10.1, module version = 1.0.0
[    14.870] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    14.870] (II) Loading sub module "ramdac"
[    14.870] (II) LoadModule: "ramdac"
[    14.870] (II) Module "ramdac" already built-in
[    14.870] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    14.870] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    14.870] (II) Loading /usr/lib/xorg/modules/libfb.so
[    14.870] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    14.870] (==) NVIDIA(0): RGB weight 888
[    14.870] (==) NVIDIA(0): Default visual is TrueColor
[    14.870] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    14.870] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
[    14.870] (EE) NVIDIA(0):     system's kernel log for additional error messages and
[    14.870] (EE) NVIDIA(0):     consult the NVIDIA README for details.
[    14.870] (EE) NVIDIA(0):  *** Aborting ***
[    14.870] (II) UnloadModule: "nvidia"
[    14.871] (II) Unloading nvidia
[    14.871] (II) UnloadModule: "wfb"
[    14.871] (II) Unloading wfb
[    14.871] (II) UnloadModule: "fb"
[    14.871] (II) Unloading fb
[    14.871] (EE) Screen(s) found, but none have a usable configuration.
[    14.871] 
Fatal server error:
[    14.871] no screens found
[    14.871] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    14.871] Please also check the log file at "/var/log/Xorg.2.log" for additional information.
[    14.871] 
[    14.871]  ddxSigGiveUp: Closing log

```

Hopefully thats enough.

I got the kernel image & headers from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc4-natty/)

I downloaded and installed the following (Filenames shortened below);

linux-image-2.6.39-rc4-amd64.deb
linux-headers-2.6.39-rc4-all.deb
linux-headers-2.6.39-rc4-amd64.deb

All installed through Software centre.

Edit, other information

```

terry@COMMODORE:~$ uname -s -r && unity --version && cat /etc/lsb-release && /usr/lib/nux/unity_support_test -p
Linux 2.6.38-8-generic
unity 3.8.16
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 470/PCI/SSE2
OpenGL version string:  4.1.0 NVIDIA 275.09.07

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
terry@COMMODORE:~$ 

```

Thanks again

---

### Post by MAFoElffen on 2011-07-10
> **terrykiwi83 said:**
> 
```

[COLOR=Red]I/O warning : failed to load external entity "/home/terry/.compiz/session/10317c746cfd6b8c08131033929277272800000018610032"
[/COLOR]
```Cheers
On that though...  That is usually a profile file / config file problem.

Open nautilus (Places), hit Ctr + H to show all the "hidden" files  and lookup "~/.compiz". Rename the folder to .compiz_old or _backup or  something like that. 

Then rename both directory "~/.gconf/apps/compiz" to "~/.gconf/apps/compiz_old".

Then reboot. You will lose all  of your  settings for compiz, but it should work again. (synaptic cleans the  system files, it doesn't clean config files in your /home/ folder).  What it will do on boot without those file... is build a new / default profile.

---

### Post by terrykiwi83 on 2011-07-10
just changed what you mentioned, rebooted and tried kernel 2.6.39 and again just purple screen (just hangs there).

At least my 2.6.38 has got rid of wobbly windows lol, I hated them just couldn't be bothered removing them :D

---

### Post by MAFoElffen on 2011-07-10
> **terrykiwi83 said:**
> Here is whats in my Xorg.0.log

```
[FONT=monospace]
[/FONT][    14.831] Current Operating System: Linux COMMODORE 2.6.39-020639rc4-generic #201104191410 SMP Tue Apr 19 14:19:01 UTC 2011 x86_64 
[    14.831] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro quiet splash vt.handoff=7 

[    14.845] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the 
[    14.845] (EE) NVIDIA(0):     system's kernel log for additional error messages and 
[    14.845] (EE) NVIDIA(0):     consult the NVIDIA README for details. 
[    14.845] (EE) NVIDIA(0):  *** Aborting *** [    14.845] (II) UnloadModule: "nvidia" 
[    14.845] (II) Unloading nvidia 
[    14.845] (II) UnloadModule: "wfb" 
[    14.845] (II) Unloading wfb 
[    14.845] (II) UnloadModule: "fb" 
[    14.845] (II) Unloading fb 
[    14.845] (EE) Screen(s) found, but none have a usable configuration. [FONT=monospace]
[/FONT][    14.845]  Fatal server error: 
[    14.845] no screens found 
[    14.845]  Please consult the The X.Org Foundation support       at http://wiki.x.org  for help.  

```
Now we find something ...  So the NVidia Kernel is booting on 2.6.39 but not on "your" 2.6.39...  I know nvidia.so loads okay on the later.

Are you comfortable using a taxt console command line without an Xsession?  

If you are I would reboot > Press the shift ket repeatedly to bring up the Grub Menu > Press "e" to get it into Edit mode > Go down to the line that starts with "linux" > delete the text " quiet splash vt.handoff=7 " and replace it with " --verbose text " > press <cntrl><x> and boot...

It should boot into a test console (running 2.6.38~rc4).  Enter your username and password... Reinstall the driver while running under that kernel.

Since the nvidia kernel worked under 2.6.38, the nvidia .run file should be fine and you shouldn't have to download any new one  You can do it just via:
```

sudo nvidia-installer --update

```That should recompile the nvidia kernel using the header files from 2.6.39~rc4...

When it finishes you can start the Xsession via
```

sudo service gdm start

```If it blackscreens, press <cntrl><alt><1> to get back to the text Console session and
```

sudo service gdm stop

```To stop that process.

---

### Post by terrykiwi83 on 2011-07-11
Thanks for the reply, am getting somewere now.

I done the editing thing in GRUB and am now actually able to run the 2.6.39 kernel but only to console.

I tried

```

sudo nvidia-installer --update

```

Got an error saying couldn't connect

Also tried running the actual .run file from nvidias website, it started up but them popped an error about something to do with it being loaded or unloaded in the kernel?

So at present stuck on the 2.6.39 console :)

When running it also mentioned to view error log so am assuming its the below one

```

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Jul 11 16:05:34 2011
installer version: 275.09.07

PATH:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

option status:
  license pre-accepted               : false
  update                             : true
  force update                       : false
  expert                             : false
  uninstall                          : false
  driver info                        : false
  precompiled interfaces             : true
  no ncurses color                   : false
  query latest version               : false
  no questions                       : false
  silent                             : false
  no recursion                       : false
  no backup                          : false
  kernel module only                 : false
  sanity                             : false
  add this kernel                    : false
  no runlevel check                  : false
  no network                         : false
  no ABI note                        : false
  no RPMs                            : false
  no kernel module                   : false
  force SELinux                      : default
  no X server check                  : false
  no cc version check                : false
  run distro scripts                 : true
  no nouveau check                   : false
  run nvidia-xconfig                 : false
  sigwinch work around               : true
  force tls                          : (not specified)
  force compat32 tls                 : (not specified)
  X install prefix                   : (not specified)
  X library install path             : (not specified)
  X module install path              : (not specified)
  OpenGL install prefix              : (not specified)
  OpenGL install libdir              : (not specified)
  compat32 install chroot            : (not specified)
  compat32 install prefix            : (not specified)
  compat32 install libdir            : (not specified)
  utility install prefix             : (not specified)
  utility install libdir             : (not specified)
  installer prefix                   : (not specified)
  doc install prefix                 : (not specified)
  kernel name                        : (not specified)
  kernel include path                : (not specified)
  kernel source path                 : (not specified)
  kernel output path                 : (not specified)
  kernel install path                : (not specified)
  precompiled kernel interfaces path : (not specified)
  precompiled kernel interfaces url  : (not specified)
  proc mount point                   : /proc
  ui                                 : (not specified)
  tmpdir                             : /tmp
  ftp mirror                         : ftp://download.nvidia.com
  RPM file list                      : (not specified)
  selinux chcon type                 : (not specified)

Using: nvidia-installer ncurses user interface
ERROR: Unable to connect to download.nvidia.com (unknown host)
ERROR: Unable to determine most recent NVIDIA Linux-x86_64 driver version.

```

So what would you think would be the next step?

---

### Post by MAFoElffen on 2011-07-11
> **terrykiwi83 said:**
> Thanks for the reply, am getting somewere now.

I done the editing thing in GRUB and am now actually able to run the 2.6.39 kernel but only to console.

I tried

```

sudo nvidia-installer --update

```Got an error saying couldn't connect

Also tried running the actual .run file from nvidias website, it started up but them popped an error about something to do with it being loaded or unloaded in the kernel?

So at present stuck on the 2.6.39 console :)

When running it also mentioned to view error log so am assuming its the below one

```

Using: nvidia-installer ncurses user interface
ERROR: Unable to connect to download.nvidia.com (unknown host)
ERROR: Unable to determine most recent NVIDIA Linux-x86_64 driver version.

```So what would you think would be the next step?
So it seems that the kernel is booting... but has other problems than just with graphics, such as with your network card and connection.

Okay... trying to figure out how to reproduce this so you still have some control to diagnose this.

Boot on kernel 2.6.38 and open a terminal.  
```

sudo gedit /etc/grub.d/40_custom

```While GEdit is open, also open /boot/grub/grub.cfg... cut (forn grub.cfg)and paste the menu item from the 2.6.39 item (to the end of the 40_custom) ... Including the 
```

Menu ...
...
}

```Go down to the kernel boot line and use the same grub menu kernel boot line options, that we used before, but also add a few more, such as this:
```

acpi_osi=Linux nomodeset --verbose text

```Then run update-grub to pick up those changes... What that did was add a menu item so you can easily use it to get to text console mode on the [COLOR=Red]2.6.39~rc4[/COLOR].  

When you get logged into the text console...
```

cp /var/log/boot.log ~/Documents/boot.log.error
ping -c 5 www.google.com > ~/Documents/ping.log

```Which will make a copy of your boot log so the we can check what errors are going on at boot... then the second will create a log of the results of a ping to the Internet. Please post these new files... You'll find them in your Documents directory.  I had you copy and create files  so you'll have access to that instance later while you are booted under 2.6.38.

I was going to have you run other tests, but it just hit me...  Reinstall the kernel while booted on 2.6.38-- If manually, reinstall in this order:
```

linux-headers-2.6.39-rc4-amd64.deb
linux-headers-2.6.39-rc4-all.deb
linux-image-2.6.39-rc4-amd64.deb

```Or maybe go into synaptic and let it figure out the order with the 3 selected for reinstall...

---

### Post by terrykiwi83 on 2011-07-11
I have no idea which part I need to cut and paste from here :\

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
set locale_dir=($root)/boot/grub/locale
set lang=en_NZ
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.39-020639rc4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
	linux	/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.39-020639rc4-generic
}
menuentry 'Ubuntu, with Linux 2.6.39-020639rc4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
	echo	'Loading Linux 2.6.39-020639rc4-generic ...'
	linux	/boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.39-020639rc4-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos1)'
	search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

```

?

---

### Post by MAFoElffen on 2011-07-11
> **terrykiwi83 said:**
> I have no idea which part I need to cut and paste from here
Cut and paste this to replace all in your 40_custom file.  Save and exit... run update-grub to pick up the change and add it to your menu.

  Remember thst you have to open it as root (sudo) to be able to edit/save this file.
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
#
menuentry 'Ubuntu Text Console, with Linux 2.6.39-020639rc4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 73c166fd-926a-4392-af7a-94d1bf8cf492
    linux    /boot/vmlinuz-2.6.39-020639rc4-generic root=UUID=73c166fd-926a-4392-af7a-94d1bf8cf492 ro [COLOR=Green]acpi_osi=Linux nomodeset --verbose text[/COLOR]
    initrd    /boot/initrd.img-2.6.39-020639rc4-generic
}
##
##     End of Menu Item

```
EDIT--> Did I mention that I modified this "especially" for you, that other people reading this would have to look at this as just an example, with the changes in [COLOR=Green]green[/COLOR]... This has his kernel version, UUID and system specs to his machine...

---

### Post by terrykiwi83 on 2011-07-14
Well you wouldn't believe what I did to fix it, basically in at the terminal I entered the following:

```

sudo -i

```

```

echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

```

```

update-initramfs -u

```

```

nvidia-installer --uninstall

```

And like magic it worked after I rebooted, straight to the nice shiny desktop.

Now my kernel reads

2.6.39.3 candela

Thanks for all your help and pointers :)

---

