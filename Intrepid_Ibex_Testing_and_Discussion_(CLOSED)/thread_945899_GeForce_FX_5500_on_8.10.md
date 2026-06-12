---
title: "GeForce FX 5500 on 8.10"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bbritt66 on 2008-10-12
Hello!

I have just upgraded to 8.10 from 8.04. I have looked through the forums to find how to get my Desktop effects working again with compiz (I can't even set the effects to "Extra" in System-Appearance-Visual Effects). I found this thread [http://ubuntuforums.org/showthread.php?t=904212](http://ubuntuforums.org/showthread.php?t=904212) and tried it but when I do that and type in compiz --replace, I get this;

Checking for Xgl: not present
Detected PCI ID for VGA:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present
Trying again with indirect rendering: Segmentation fault (core dumped)
not present
aborting and using fallback: /usr/bin/metacity

and it hangs there, have to close the terminal with mouse click on "X".

I have the Restricted driver for NVIDIA (173 Recommended) enabled because when I try to install the driver from NVIDIA (173.14.09) I get the message "Could not build Kernel module".

I have also tried uninstalling/re-installing compiz with no success. 

Because of not even being able to set Desktop Effects to Extra in Appearance, it seems to me the driver available and recommended by Ubuntu is not really working because also when I look at the settings for it, there is no Xgl there either and I cannot install Xgl in Synaptic because it will not allow me to (I get a message telling me that the package is mentioned in a database but not downloaded or is obsoleted). I noticed in Synaptic that Ubuntu has another package that is supposed to be providing Xgl but evidently is not.

Any help would be greatly appreciated!
Thanks!

---

### Post by manimal347 on 2008-10-12
Interesting. Support for your card was just dropped from the new 1.7xx driver, but you made it sound like your running the 1.73xx legacy driver. Doublecheck that's what your installing, but I think you've got the right one.

---

### Post by bbritt66 on 2008-10-12
> **manimal347 said:**
> Interesting. Support for your card was just dropped from the new 1.7xx driver, but you made it sound like your running the 1.73xx legacy driver. Doublecheck that's what your installing, but I think you've got the right one.

Thanks for your reply! Yes, unfortunately my card has been dropped by the new driver and so I have to go with the one NVIDIA recommends (legacy) or the one that Ubuntu wants to install. I am forced at the moment to go with the one Ubuntu wants to install/enable to even see my screen correctly. However there are no Effects with that driver. 

What is really throwing me is that I cannot install the NVIDIA driver (even the one I used on 8.04) because of the message that I get "Could not build kernel module". I drop to a terminal, stop gdm and run the sh with sudo as I've done many times with 8.04 and I accept the license, it tells me there is no precompiled kernel module and asks to download one(as always it does) then I tell it to build one and it goes into doing so but fails saying it could not build kernel module.

So I look in /var/log/nvidia-installer.log to see what went wrong and it tells me that the sources and headers are not available. So I look for them in Synaptic but can't find them. That's why I'm forced to go with enabling the driver Ubuntu wants me to. After reboot, it sees my card correctly and even identifies it, but does not offer any effects because it says there is no glx.

I'm getting really confused.
Thanks again!

---

### Post by milliman on 2008-10-12
bbritt66:

I had the same problem twice when the kernels changed with my GeForce FX 5200 Ultra and Ibex.  First of all your video card will work with Ibex so Compiz will function properly.  I got it working on my system with version 173 of the nVidia drivers.  The problem is that my instructions may not be the most accurate.  

I tried activating it through the Hardware Drivers application, but it didn't work.  First to to System->Administration->Hardware Drivers and see if you have version 173 of the driver listed.  If it is then, click the "Activate" button and see if the indicator goes green.  If it goes green, either reboot or restart gdm.  If not, then hopefully it retrieved the driver and kernel modules.  Open Synaptic Package Manager and verify that nvidia-173-kernel-source, nvidia-173-modaliases, and nvidia-glx-173 are installed.  If not, then install them.  If so then verify that you have linux-headers and linux-headers-generic installed.

If they are or are not installed reinstall them.  This will trigger a kernel rebuild with dkms which should build the nvidia.ko module into your kernel.  Restart gdm or reboot.  Your driver should load and you can turn on Compiz.

Good Luck

---

### Post by bbritt66 on 2008-10-12
> **milliman said:**
> bbritt66:

I had the same problem twice when the kernels changed with my GeForce FX 5200 Ultra and Ibex.  First of all your video card will work with Ibex so Compiz will function properly.  I got it working on my system with version 173 of the nVidia drivers.  The problem is that my instructions may not be the most accurate.  

I tried activating it through the Hardware Drivers application, but it didn't work.  First to to System->Administration->Hardware Drivers and see if you have version 173 of the driver listed.  If it is then, click the "Activate" button and see if the indicator goes green.  If it goes green, either reboot or restart gdm.  If not, then hopefully it retrieved the driver and kernel modules.  Open Synaptic Package Manager and verify that nvidia-173-kernel-source, nvidia-173-modaliases, and nvidia-glx-173 are installed.  If not, then install them.  If so then verify that you have linux-headers and linux-headers-generic installed.

If they are or are not installed reinstall them.  This will trigger a kernel rebuild with dkms which should build the nvidia.ko module into your kernel.  Restart gdm or reboot.  Your driver should load and you can turn on Compiz.

Good Luck

I must say I feel pretty stupid... I had said earlier that I couldn't find the headers and such in Synaptic... I was searching wrong. Anyway, I follow ed these directions to the T and I still can't get it to work. It does however allow me to get a decent screen resolution, but I can't even do something as simple as System-Appearance-Extras because it says Desktop effects could not be activated (due to driver, which is what I was beginning to think it was anyway... something is wrong with the driver and I can't install the one from NVIDIA because it keeps bombing at building the kernel module).

Thanks for the help though. There has to be a way to get a driver working for this card. The NVIDIA site has 2 (only one recommended though) for linux and I've tried both and both bomb at building the kernel module.

Is there something with this particular kernel that prevents modules from being built? I had no problems whatsoever building modules ever up until I upgraded to 8.10 and I actually had to build them several times, all with no problem. Really strange.

---

### Post by milliman on 2008-10-12
Do you have all of the dependencies to build a kernel?  What error message do you receive?  You may want to make sure that you only have the director nvidia-173.14.12 in /usr/src.  Remove all other nvidia source code.  Then rebuild the kernel.

---

### Post by bbritt66 on 2008-10-13
OK, I have checked and Synaptic shows I have all I need to do what I need to do... kernel source, headers and so on. However, when I try to install either of the NVIDIA drivers, even the one recommended for my card, I get the same error message that it is "unable to build kernel module". So I have posted here below the output of /var/log/nvidia-installer.log. It is quite lengthy so I apologize for that, but I can't figure out where I'm going wrong with this. I've never had trouble with modules or compilation of a kernel before. I get this same message no matter which driver I try to install.

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Mon Oct 13 02:29:11 2008
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
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 173.14.09.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
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
   /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz8264/NVIDIA-Linux-x86-173.14.0
   9-pkg1/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.2/include -D__KERNEL
   __  -Iinclude  -I/usr/src/linux-headers-2.6.27-7-generic/arch/x86/include -i
   nclude include/linux/autocon
   f.h -Iubuntu/include  -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-
   strict-aliasing -fno-common -Werror-implicit-function-declaration -O2 -m32 -
   msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -ma
   rch=i586 -mtune=generic -ffreestanding -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/
   mach-default -fno-stack-protector -fno-omit-frame-pointer -fno-optimize-sibl
   ing-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -I/tmp/selfgz8
   264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv -Wall -Wimplicit -Wreturn-typ
   e -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mul
   tichar -Werror -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DM
   ODULE -DNVRM -DNV_VERSION_STRING=\"173.14.09\" -UDEBUG -U_DEBUG -DNDEBUG -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MOD
   NAME=KBUILD_STR(nvidia)" -c -o /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pk
   g1/usr/src/nv/.tmp_nv.o /tmp/selfgz8
   264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
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
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:19,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:1969: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:52,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from include/asm/pci.h:94,
                    from include/linux/pci.h:983,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:86,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv-linux.h:107:27
   : error: asm/semaphore.h: No such file or directory
   In file included from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv-linux.h:109,
                    from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
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
   In file included from /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
   c/nv/nv.c:14:
   /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv-linux.h: In fu
   nction ‘nv_execute_on_all_cpus’:
   /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv-linux.h:674: e
   rror: too many arguments to function ‘on_each_cpu’
   /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c: In function
   ‘nv_kern_cpu_callback’:
   /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c:1299: error:
   too many arguments to function ‘smp_call_function’
   /tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.c:1306: error:
   too many arguments to function ‘smp_call_function’
   make[3]: *** [/tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/src/nv/nv.
   o] Error 1
   make[2]: *** [_module_/tmp/selfgz8264/NVIDIA-Linux-x86-173.14.09-pkg1/usr/sr
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
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Xgen on 2008-10-13
I also receive the 'unable to build kernel' message if installing the 173.14.12 driver downloaded from the Nvidia site. Happens with the 2.6.27 linux kernels, but there is a patch which WFM that is applied to the Nvidia driver which corrects the problem (bottom post).

[http://www.nvnews.net/vbulletin/showthread.php?t=118595]("http://www.nvnews.net/vbulletin/showthread.php?t=118595")

---

### Post by bbritt66 on 2008-10-13
> **Xgen said:**
> I also receive the 'unable to build kernel' message if installing the 173.14.12 driver downloaded from the Nvidia site. Happens with the 2.6.27 linux kernels, but there is a patch which WFM that is applied to the Nvidia driver which corrects the problem (bottom post).

[http://www.nvnews.net/vbulletin/showthread.php?t=118595]("http://www.nvnews.net/vbulletin/showthread.php?t=118595")

Thanks! I downloaded the patch. How did you go about applying it or have the developers already applied it?

---

### Post by Xgen on 2008-10-13
It has been quite a while since I did the patch...so hopefully this works:

Make sure 'patch' is installed...Synaptic-->patch (optional 'patchutils').
Place patch file in the same folder as the nvidia driver.
Best to keep a copy of the nvidia driver.

cd (location of nvidia driver)
patch -p0 < (patch-file-name-here)

MORE DETAILED INFORMATION: Google: 'How to patch a linux file'

---

### Post by bbritt66 on 2008-10-14
Ok, sorry for the delay. Here is the output, the error message while applying the patch;

diff: NVIDIA-Linux-x86-173.14.12-pkg0.orig/usr/src/nv/nv.c: No such file or directory
diff: NVIDIA-Linux-x86-173.14.12-pkg0/usr/src/nv/nv.c: No such file or directory
NVIDIA_173.14.12_2.6.27.patch: 2: ---: not found
NVIDIA_173.14.12_2.6.27.patch: 3: +++: not found
NVIDIA_173.14.12_2.6.27.patch: 4: @@: not found
NVIDIA_173.14.12_2.6.27.patch: 6: Syntax error: word unexpected (expecting ")")

EDIT: I'm giving up. Thanks to all of you for your time and help! I really appreciate it! I've backed up all my stuff (nearly 40 gig, it builds up over time!) and going to just reload 8.04. To me it's better and cheaper than going out and buying a new card just because I've upgraded. Thanks again!

---

