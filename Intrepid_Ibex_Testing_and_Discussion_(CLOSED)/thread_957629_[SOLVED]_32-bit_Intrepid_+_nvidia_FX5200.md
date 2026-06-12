---
title: "[SOLVED] 32-bit Intrepid + nvidia FX5200"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Daimoneze on 2008-10-24
The newer package (177.xx) ignores the device even though it's what NVidia provides when you specify this device. So I went and got the 173.xx package that the newer package recommends. Then the error comes:

```
ERROR: Unable to build the NVIDIA kernel module.
```

Here is the log:

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Oct 24 14:25:05 2008

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
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27-7-generic/build'
-> Kernel output path: '/lib/modules/2.6.27-7-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27-7-generi
   c/build SYSOUT=/lib/modules/2.6.27-7-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.27-7-generic/build SUBDIRS=
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/.tmp_versi
   ons ; rm -f /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/.tmp_ve
   rsions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz20219/NVIDIA-Linux-x86-173.08-
   pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/.nv.o.
   d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL__
    -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubun
   tu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-ali
   asing -fno-common -Werror-implicit-function-declaration -O2 -m32 -msoft-floa
   t -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i586 -
   mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchronous-unwin
   d-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-defau
   lt -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibling-calls 
   -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz20219/NVIDI
   A-Linux-x86-173.08-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -
   Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werr
   or -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM
   -DNV_VERSION_STRING=\"173.08\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_
   STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(
   nvidia)" -c -o /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/.tmp
   _nv.o /tmp/selfgz20219/NVIDIA-Linux
   -x86-173.08-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv.c:14:
   include/asm/bitops.h: In function â€˜set_bitâ€™:
   include/asm/bitops.h:60: warning: pointer of type â€˜void *â€™ used in arith
   metic
   include/asm/bitops.h: In function â€˜clear_bitâ€™:
   include/asm/bitops.h:97: warning: pointer of type â€˜void *â€™ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/prefetch.h: In function â€˜prefetch_rangeâ€™:
   include/linux/prefetch.h:57: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv-linux.h:19,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/sched.h: In function â€˜object_is_on_stackâ€™:
   include/linux/sched.h:1969: warning: pointer of type â€˜void *â€™ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv-linux.h:86,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/scatterlist.h: In function â€˜sg_virtâ€™:
   include/linux/scatterlist.h:199: warning: pointer of type â€˜void *â€™ used 
   in arithmetic
   In file included from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv.c:14:
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv-linux.h:107:27: 
   error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv-linux.h:109,
                    from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv.c:14:
   include/linux/highmem.h: In function â€˜zero_user_segmentsâ€™:
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type â€˜void *â€™ used in a
   rithmetic
   In file included from /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv/nv.c:14:
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv-linux.h: In func
   tion â€˜nv_execute_on_all_cpusâ€™:
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv-linux.h:671: err
   or: too many arguments to function â€˜on_each_cpuâ€™
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c: In function â
   €˜nvos_proc_createâ€™:
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:614: error: â€
   ˜proc_root_driverâ€™ undeclared (first use in this function)
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:614: error: (E
   ach undeclared identifier is reported only once
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:614: error: fo
   r each function it appears in.)
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c: In function â
   €˜nv_kern_cpu_callbackâ€™:
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:1289: error: t
   oo many arguments to function â€˜smp_call_functionâ€™
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:1296: error: t
   oo many arguments to function â€˜smp_call_functionâ€™
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c: In function â
   €˜nv_kern_vma_nopageâ€™:
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:1846: error: â
   €˜NOPAGE_SIGBUSâ€™ undeclared (first use in this function)
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c: At top level:
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:1853: error: u
   nknown field â€˜nopageâ€™ specified in initializer
   /tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.c:1853: warning:
   initialization from incompatible pointer type
   make[3]: *** [/tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/nv/nv.o]
   Error 1
   make[2]: *** [_module_/tmp/selfgz20219/NVIDIA-Linux-x86-173.08-pkg1/usr/src/
   nv] Error 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

I do what have what I believe to be the necessary packages in order to build the kernel module including make, libc6, and the kernel headers. 

Any suggestions?

---

### Post by Daimoneze on 2008-10-25
Hmm. No idea so far?

---

### Post by kc0bfv on 2008-10-25
Hey!  I had this problem up until about 10 minutes ago.  Check out this site:
[http://www.nvnews.net/vbulletin/showthread.php?t=121295]("http://www.nvnews.net/vbulletin/showthread.php?t=121295")

It links to a patch here:
[http://kanotix.com/files/173.14.12/NVIDIA_173.14.12_2.6.27.patch]("http://kanotix.com/files/173.14.12/NVIDIA_173.14.12_2.6.27.patch")

Which then can be installed with the following command:
./NVIDIA-Linux-x86-173.14.12-pkg1.run --apply-patch NVIDIA_173.14.12_2.6.27.patch

For me, the NVIDIA installer patched the files, then rebuilt a new .run installer file and tried to execute that .run file.  It failed to execute the file, I believe because I was running as sudo, so I just ran the file it created:
./NVIDIA-Linux-x86-173.14.12-pkg1-custom.run

There were a few compilation warnings that screwed up the UI, but everything worked in the end.

Edit: Oh yeah, I'm running Debian.  GO DEBIAN!

---

### Post by Daimoneze on 2008-10-26
Alright. That got me pretty exited but it failed. I think I'm pretty close though and just suffering from noobitis. 

```
bash: ./NVIDIA-Linux-x86-177.80-pkg1.run: Permission denied

```
I got a permission error (although my user is owner and the files are on my desktop) so I ran it with sh and it worked (I don't know if that's any different but it doesn't seem so).Then I got this:

```
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 177.80.............................................................................................................................................................................................................................................................................................
patching file usr/src/nv/nv.c
Hunk #1 FAILED at 1296.
1 out of 1 hunk FAILED -- saving rejects to file usr/src/nv/nv.c.rej
patching file usr/src/nv/nv-linux.h
Hunk #1 FAILED at 104.
Hunk #2 FAILED at 668.
2 out of 2 hunks FAILED -- saving rejects to file usr/src/nv/nv-linux.h.rej
patching file usr/src/nv/os-interface.c
Hunk #1 FAILED at 48.
Hunk #2 FAILED at 708.
2 out of 2 hunks FAILED -- saving rejects to file usr/src/nv/os-interface.c.rej
Failed to apply patch file "/home/toast/Desktop/NVIDIA_patch".
```

I'm not sure how to interpret that other than it didn't like the code from the .run at those lines. I looked for those "reject" outputs but I couldn't find them. :frown:

---

### Post by psyke83 on 2008-10-26
I cannot emphasise this enough: **do not install the nvidia drivers manually.**

Seriously, why would you want to give yourself a headache by installing the drivers manually? Aside from the mess of a manual installation (which leaves a lot of cruft, files which cannot be accounted for, and Mesa symlinks getting broken), each time there's a non-trivial kernel update you'll have to manually rebuild the drivers. 

The official repositories contain the "nvidia-glx-177" and "nvidia-glx-173" packages, of which the latter suits your card. These packages are fully supported, and are capable of dynamically rebuilding the nvidia kernel module via DKMS when necessary.

My recommendation: Run the nvidia installer again with the --uninstall parameter, then install the nvidia-glx-173 package (via Synaptic/apt-get or Jockey).

---

### Post by Teamgeist on 2008-10-26
Yeah, the HIGHLY recommended and the RIGHT way to install NVIDIA and ATI drivers is through

System--> Administration--> Hardware Drivers

It will find and install the right driver for you.
Plus you will not have to rebuild and reinstall the driver after a kernel update thanks to dkms, as mentioned above.

---

### Post by Daimoneze on 2008-10-26
> I cannot emphasise this enough: do not install the nvidia drivers manually.

Seriously, why would you want to give yourself a headache by installing the drivers manually? Aside from the mess of a manual installation (which leaves a lot of cruft, files which cannot be accounted for, and Mesa symlinks getting broken), each time there's a non-trivial kernel update you'll have to manually rebuild the drivers.

The official repositories contain the "nvidia-glx-177" and "nvidia-glx-173" packages, of which the latter suits your card. These packages are fully supported, and are capable of dynamically rebuilding the nvidia kernel module via DKMS when necessary.

My recommendation: Run the nvidia installer again with the --uninstall parameter, then install the nvidia-glx-173 package (via Synaptic/apt-get or Jockey).

> Yeah, the HIGHLY recommended and the RIGHT way to install NVIDIA and ATI drivers is through

System--> Administration--> Hardware Drivers

It will find and install the right driver for you.
Plus you will not have to rebuild and reinstall the driver after a kernel update thanks to dkms, as mentioned above. 

I have no issue with installing the repo drivers as long as they *function* the same as the ones provided by NVidia. I'm downloading the repo drivers now and am going to try them out. Not having to rebuild after kernel updates would be nice, but it's not really that strenuous.

---

### Post by Daimoneze on 2008-10-27
Well, with the repo drivers I can't seem to get compiz to turn on. I have reinstalled compiz after installing the driver and also grabbed simple ccsm. Any particular suggestions?

---

### Post by psyke83 on 2008-10-27
> **Daimoneze said:**
> Well, with the repo drivers I can't seem to get compiz to turn on. I have reinstalled compiz after installing the driver and also grabbed simple ccsm. Any particular suggestions?

Check your dmesg & Xorg.0.log for errors relating to the NVIDIA kernel module. More than likely, there's obsolete kernel modules (or libraries) interfering with the official packages.

---

### Post by daitau on 2008-10-28
> **Daimoneze said:**
> Well, with the repo drivers I can't seem to get compiz to turn on. I have reinstalled compiz after installing the driver and also grabbed simple ccsm. Any particular suggestions?
Make sure you use the driver 'nvidia' instead of 'nv' in xorg.conf. Also make sure the package linux-headers is installed for DKMS to work. For some reasons it was removed automatically when I upgraded my system from Hardy.

---

### Post by Daimoneze on 2008-10-28
Alright, I did get X to start with no problems after changing "nv" to "nvidia" (I forgot I changed it when it was bugging out initially). I do see the logo when X is starting now.

> Check your dmesg & Xorg.0.log for errors relating to the NVIDIA kernel module. More than likely, there's obsolete kernel modules (or libraries) interfering with the official packages.
I'm not sure where to find these logs. If someone would be so kind as to post their locations here I'll examine and post them. I would like to get rid of any old kernel modules if they're there. 

Still no compiz after changing xorg.conf.

---

