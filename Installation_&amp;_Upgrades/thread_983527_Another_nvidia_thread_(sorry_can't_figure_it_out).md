---
title: "Another nvidia thread (sorry can't figure it out)"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by cashmoney on 2008-11-15
I followed tseliot's guide to kernel compilation [http://ubuntuforums.org/showthread.php?t=56835](http://ubuntuforums.org/showthread.php?t=56835) and installing nvidia drivers [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368).

I cannot for the life of me get nvidia drivers to install properly.  When I get to sh NVIDIA-linux-x86-173.14.12-pkg.run  It

a) doesn't find a precompiled kernel interface and it doesn't find one on [ftp://download.nvidia.com](ftp://download.nvidia.com).
b)Then it goes the installer will need to compile a new kernel interface.  The progress bar goes to 100% when it compiles but I get  ERROR: Unable to build the NVIDIA kernel module.

If anyone has any ideas let me know.

lspci 
```
VGA compatible controller: nVidia Corporation Quadro NVS 135M (rev a1)
```

uname -r
```
2.6.27.6-nates

ls /usr/src/
linux
linux-2.6.27.6
linux-headers-2.6.24-16
linux-headers-2.6.24-16-generic
linux-headers-2.6.24-21
linux-headers-2.6.24-21-generic
linux-headers-2.6.27.6-nates
linux-headers-2.6.27.6-nates_2.6.24.6-nates-10.00.Custom_i386.deb
linux-image-2.6.27.6-nates_2.6.24.6-nates-10.00.Custom_i386.deb
```



```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Nov 15 19:23:22 2008
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
-> Installing NVIDIA driver version 173.14.12.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: No)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.27.6-nates/source'
-> Kernel output path: '/lib/modules/2.6.27.6-nates/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.27.6-nates/
   source SYSOUT=/lib/modules/2.6.27.6-nates/build'...
   NVIDIA: calling KBUILD...
   make CC=cc KBUILD_OUTPUT=/lib/modules/2.6.27.6-nates/build KBUILD_VERBOSE=1 
   -C /lib/modules/2.6.27.6-nates/source SUBDIRS=/tmp/selfgz13827/NVIDIA-Linux-
   x86-173.14.12-pkg1/usr/src/nv modules
   make -C /lib/modules/2.6.27.6-nates/build \
   	KBUILD_SRC=/usr/src/linux-2.6.27.6 \
   	KBUILD_EXTMOD="/tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv"
   -f /usr/src/linux-2.6.27.6/Makefile \
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
   mkdir -p /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_ve
   rsions ; rm -f /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.
   tmp_versions/*
   make -f /usr/src/linux-2.6.27.6/scripts/Makefile.build obj=/tmp/selfgz13827/
   NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.nv
   .o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.2.4/include -D__KERNE
   L__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.27.6/include -I/usr/src/linux-
   2.6.27.6/arch/x86/include -include include/linux/autoconf.h  -I/tmp/selfgz13
   827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv -Wall -Wundef -Wstrict-protot
   ypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-functi
   on-declaration -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mprefe
   rred-stack-boundary=2 -march=i686 -mtune=generic -ffreestanding -pipe -Wno-s
   ign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno
   -3dnow -I/usr/src/linux-2.6.27.6/include/asm-x86/mach-default -Iinclude/asm-
   x86/mach-default -fno-stack-protector -fomit-frame-pointer -g -Wdeclaration-
   after-statement -Wno-pointer-sign  -I/tmp/selfgz13827/NVIDIA-Linux-x86-173.1
   4.12-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar
   -subscripts 
   -Wparentheses -Wpointer-arith -Wno-multichar -Werror -MD -Wsign-compare -Wno
   -cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"173
   .14.12\" -UDEBUG -U_DEBUG -DNDEBUG -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /tmp/se
   lfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/.tmp_nv.o /tmp/selfgz13
   827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:19,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/asm/bitops.h: In function ‘set_bit’:
   include/asm/bitops.h:60: warning: pointer of type ‘void *’ used in arith
   metic
   include/asm/bitops.h: In function ‘clear_bit’:
   include/asm/bitops.h:97: warning: pointer of type ‘void *’ used in arith
   metic
   In file included from include/linux/list.h:6,
                    from include/linux/preempt.h:11,
                    from include/linux/spinlock.h:50,
                    from include/linux/seqlock.h:29,
                    from include/linux/time.h:8,
                    from include/linux/timex.h:57,
                    from include/linux/sched.h:54,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:19,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:19,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1971: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:86,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:107:2
   7: error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv-linux.h:109,
                    from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:137: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv/nv.c:14:
   /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h: In f
   unction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv-linux.h:674: 
   error: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c: In functio
   n ‘nv_kern_cpu_callback’:
   /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1299: error
   : too many arguments to function ‘smp_call_function’
   /tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv.c:1306: error
   : too many arguments to function ‘smp_call_function’
   make[4]: *** [/tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/src/nv/nv
   .o] Error 1
   make[3]: *** [_module_/tmp/selfgz13827/NVIDIA-Linux-x86-173.14.12-pkg1/usr/s
   rc/nv] Error 2
   make[2]: *** [sub-make] Error 2
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

---

### Post by inobe on 2008-11-15
never setup nvidia in ubuntu given that it only needs enabled.

in opensuse that was common after kernel updates to reinstall, it didn't matter because their was always a new update from nvidia.

a) is okay
b) is okay too until it fails.

that failing point says you don't have gcc and linux kernel development installed.

---

### Post by cashmoney on 2008-11-15
> **inobe said:**
> never setup nvidia in ubuntu given that it only needs enabled.

in opensuse that was common after kernel updates to reinstall, it didn't matter because their was always a new update from nvidia.

a) is okay
b) is okay too until it fails.

that failing point says you don't have gcc and linux kernel development installed.

gcc is installed and I ran sudo apt-get install linux-kernel-devel
and retried same thing.  Installation has failed.

---

### Post by inobe on 2008-11-15
check one more thing, g++

its a gnu c++ compiler, if you have that in your system' have you tried different driver, also are you running 64 bit os ?

edit: what about **build-essentials** 

this thread makes me want to tun nvidia's beta for pure video :KS

---

### Post by inobe on 2008-11-15
i will attempt to install the driver, if i manage to' i will post a howto in this thread.

:)

---

### Post by cashmoney on 2008-11-15
I got it to work.  I will post up how I did it when I redo it so I don't miss a step.

Thanks for the help.

Nate

---

### Post by inobe on 2008-11-15
thats great, i can't wait to see the steps you've used :guitar:

i have a second install of ubuntu intrepid x86 64 bit, i will try the driver install after all these updates are done.

i will attempt it on this install, my other install is tweaked and don't wish to bork it, not even in the slightest !

given this is a fresh install i will be able to list everything i needed to install in order to achieve an nvidia manual installation.

this may take a wile

edit: for those that attempt it' keep in mind a kernel update will break nvidia's module and you will be forced into the infamous command line of darkness.

---

### Post by cashmoney on 2008-11-15
So far I have only got the video drivers to work on the newest kernel I installed.  Right now I don't have a fall back kernel in case something really messes up with 2.6.27.6

I got it to work and here is how 32-bit Ubuntu.  As of this writing this is the latest version of stable Nvidia Drivers 11-15-2008 Driver version 177.82 Thanks to Zander from the NVIDIA corporation for part of this how to. 

1) Check if your card is supported.  [http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/appendix-a.html")

2) If it is then download the drivers from here.  [http://www.nvidia.com/object/linux_display_ia32_177.82.html](http://www.nvidia.com/object/linux_display_ia32_177.82.html)


3)  
```
apt-get install gcc make pkg-config xserver-xorg-dev
```
    Also make sure you have the headers package installed for your kernel

```
uname -r
sudo apt-get install linux-headers-'uname -r'
```
replace 'uname -r' in the 2nd command with the output of the first command.

4) Now we remove all of the old nvidia drivers

```
apt-get remove nvid(tab twice)
```

Now just do sudo apt-get purge on everything listed in the previous command.  I tried doing sudo apt-get remove nvidia* and it didn't work for some reason.

```
rm /etc/init.d/nvidia-kernel
rm /etc/init.d/nvidia-glx
```
    
5) The next part was taken from NVIDIA's website    

All I had to do was 
```
 rm /lib/linux-restricted-modules/.nvidia_new_installed
```

> If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed[http://www.nvnews.net/vbulletin/showthread.php?t=72490]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

6)I moved the downloaded NVIDIA driver to /usr/src.  
    ```
sudo mv /Source to file/NVIDIA-Linux-x86-177.82-pkg1.run /usr/src
```

Next I shut down the GUI hit ctrl+alt+F1 put in your credentials and type ```
/etc/init.d/gdm stop
```

7)
```
cd /usr/src
sh NVIDIA-Linux-x86-177.82-pkg1.run /usr/src
```

After it ran through that the installer automatically configures xorg.conf and makes a backup called xorg.conf_backup

```
sync;sync;sync
sudo shutdown -r now
```

When your pc boots up viola using nvidia driver

EDIT:actually it works for the kernel you configured it for.  I haven't figured out how to get it to work on any of my other kernels I have installed.

---

### Post by inobe on 2008-11-15
great looking howto.

what fixed the failed install' or should i say' what did you correct to get the module to install ?

---

### Post by cashmoney on 2008-11-15
> **inobe said:**
> great looking howto.

what fixed the failed install' or should i say' what did you correct to get the module to install ?

newer driver package and I didn't have pkg-config (or xserver-xorg-dev)  not 100% sure

---

