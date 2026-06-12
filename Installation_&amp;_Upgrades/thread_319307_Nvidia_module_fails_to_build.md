---
title: "Nvidia module fails to build"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by DarkBabar on 2006-12-15
I'm trying to build the Nvidia module for my new custom RT-kernel, but the build fails. I've tried make-kpkg and module-assistant and the result is the same.
```
/usr/bin/make  -f debian/rules clean
make[1]: Entering directory `/usr/src/modules/nvidia-kernel'
# select which makefile to use.
rm -f /usr/src/modules/nvidia-kernel/nv/Makefile || true
if [ 6 = 6  ]; then \
	     cd /usr/src/modules/nvidia-kernel/nv ; \
	     ln -s Makefile.kbuild Makefile ; \
	     cd .. ; \
	     if [ 0 = 1 ]; then \
	     	dpatch apply 01_sysfs ; \
		dpatch status 01_sysfs >patch-stamp ; \
		dpatch apply 02_pcialias ; \
               	dpatch status 02_pcialias >>patch-stamp ; \
	     fi \
	fi
if [  6 = 4  ]; then \
	     cd /usr/src/modules/nvidia-kernel/nv ; \
	     ln -s Makefile.nvidia Makefile ; \
	     cd .. ; \
	fi
if [ -e patch-stamp ]; then \
	   dpatch deapply-all ; \
	   rm -rf patch-stamp debian/patched ; \
	fi   
if [ -f /usr/src/modules/nvidia-kernel/debian/control.template ]; then \
		cp  /usr/src/modules/nvidia-kernel/debian/control.template /usr/src/modules/nvidia-kernel/debian/control; \
	fi
dh_testroot
rm -f build-stamp configure-stamp
/usr/bin/make clean SYSSRC=/usr/src/linux-headers-2.6.19-rt11 -C /usr/src/modules/nvidia-kernel/nv -f Makefile 
make[2]: Entering directory `/usr/src/modules/nvidia-kernel/nv'
rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
rm -f -f stprof stprof.o symtab.h
rm -f -rf .tmp_versions
make[2]: Leaving directory `/usr/src/modules/nvidia-kernel/nv'
rm -f /usr/src/modules/nvidia-kernel/nv/Makefile || true; 	
rm /usr/src/modules/nvidia-kernel/nv/gcc-check
rm /usr/src/modules/nvidia-kernel/nv/cc-sanity-check
dh_clean
rm /usr/src/modules/nvidia-kernel/debian/control
rm /usr/src/modules/nvidia-kernel/debian/dirs
rm /usr/src/modules/nvidia-kernel/debian/override
make[1]: Leaving directory `/usr/src/modules/nvidia-kernel'
echo "ROOT_CMD = "
ROOT_CMD = 
/usr/bin/make  -f debian/rules binary_modules
make[1]: Entering directory `/usr/src/modules/nvidia-kernel'
# select which makefile to use.
rm -f /usr/src/modules/nvidia-kernel/nv/Makefile || true
if [ 6 = 6  ]; then \
	     cd /usr/src/modules/nvidia-kernel/nv ; \
	     ln -s Makefile.kbuild Makefile ; \
	     cd .. ; \
	     if [ 0 = 1 ]; then \
	     	dpatch apply 01_sysfs ; \
		dpatch status 01_sysfs >patch-stamp ; \
		dpatch apply 02_pcialias ; \
               	dpatch status 02_pcialias >>patch-stamp ; \
	     fi \
	fi
if [  6 = 4  ]; then \
	     cd /usr/src/modules/nvidia-kernel/nv ; \
	     ln -s Makefile.nvidia Makefile ; \
	     cd .. ; \
	fi
#nothing here anymore
touch configure-stamp
if [ -f /usr/src/modules/nvidia-kernel/debian/control.template ]; then \
		cp  /usr/src/modules/nvidia-kernel/debian/control.template /usr/src/modules/nvidia-kernel/debian/control; \
	fi
dh_testdir
dh_testroot
PATCHLEVEL = 6 
Kernel compiler version : 4.1.1
Detected compiler version : 4.1.1
Using compiler gcc-4.1 version 4.1.1
touch /usr/src/modules/nvidia-kernel/nv/gcc-check
touch /usr/src/modules/nvidia-kernel/nv/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc-4.1"  /usr/bin/make -C /usr/src/modules/nvidia-kernel/nv -f Makefile SYSSRC=/usr/src/linux-headers-2.6.19-rt11   KBUILD_PARAMS="-C /usr/src/linux-headers-2.6.19-rt11 SUBDIRS=/usr/src/modules/nvidia-kernel/nv" module;
make[2]: Entering directory `/usr/src/modules/nvidia-kernel/nv'
Your kernel was configured to include rivafb support!

The rivafb driver conflicts with the NVIDIA driver, please
reconfigure your kernel and *disable* rivafb support, then
try installing the NVIDIA kernel module again.

*** Failed rivafb sanity check. Bailing out! ***

make[2]: *** [rivafb-sanity-check] Error 1
make[2]: Leaving directory `/usr/src/modules/nvidia-kernel/nv'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/nvidia-kernel'
make: *** [kdist_image] Error 2

```
The error message seems clear enough. Just remove rivafb support, and I'll be fine. Unfortunately that doesn't help. I keep getting the same error message, even though I've disabled support for frame buffer entirely. I'm really lost here, and would greatly appreciate any help.

---

### Post by DarkBabar on 2006-12-17
Bump

---

### Post by Ptero-4 on 2006-12-17
Try recompiling your kernel without the old NVidia Riva drivers (both DRI and framebuffer ones) and you should be fine there.

---

### Post by DarkBabar on 2006-12-18
> **Ptero-4 said:**
> Try recompiling your kernel without the old NVidia Riva drivers (both DRI and framebuffer ones) and you should be fine there.

I've deselected
Device Drivers -> Graphics support -> Support for frame buffer devices
I can't find any reference to Riva anywhere else, but if there is some other option i should deselect, please direct me to that option. I'd be most grateful.

---

### Post by po0f on 2006-12-18
DarkBabar,

What's the output of:
```
[FONT="Courier New"]$ grep RIVA /path/to/kernel/src/.config[/FONT]
```

---

### Post by DarkBabar on 2006-12-18
> **po0f said:**
> DarkBabar,

What's the output of:
```
[FONT="Courier New"]$ grep RIVA /path/to/kernel/src/.config[/FONT]
```
CONFIG_IPV6_PRIVACY=y

---

### Post by DarkBabar on 2006-12-19
Bumping again.

---

### Post by DarkBabar on 2006-12-20
Bumping once more.

---

### Post by DarkBabar on 2006-12-21
Still hoping for a solution.

---

### Post by DarkBabar on 2006-12-22
Sigh...

---

### Post by po0f on 2006-12-22
DarkBabar,

Is there anyway you can post a screenshot of this?  Run `make menuconfig` from a terminal in X and post a screenshot if you can after navigating to "Device Drivers -> Graphics support".

---

### Post by DarkBabar on 2006-12-22
> **po0f said:**
> DarkBabar,

Is there anyway you can post a screenshot of this?  Run `make menuconfig` from a terminal in X and post a screenshot if you can after navigating to "Device Drivers -> Graphics support".

[[IMG]http://img249.imageshack.us/img249/4726/snapshot1jm9.th.png[/IMG]](http://img249.imageshack.us/my.php?image=snapshot1jm9.png)
Click the thumbnail for full view.

---

### Post by DarkBabar on 2006-12-26
Merry Christmas! (bump)

---

### Post by DarkBabar on 2006-12-29
Still seeking a solution.

---

### Post by shadower on 2007-01-06
Bit of a bump, but I'm also having the same problem. So you're not alone!

Output of make-kpkg modules_image;

```
exec debian/rules  DEBIAN_REVISION=2.6.20-rc2-mm1-10.00.Custom  modules_image 
for module in /usr/src/modules/nvidia-kernel ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.20-rc2-mm1" KSRC="/usr/src/linux" \
                             KMAINT="Paul Fraser" KEMAIL="pfraser@gmail.com"                                                                                                                                       
  \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Paul Fraser"        \
                             KPKG_EXTRAV_ARG=""        \
                             ARCH="i386"                  \
                             KDREV="2.6.20-rc2-mm1-10.00.Custom" kdist_image; th                                                                                                                                   
en    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done
make[1]: Entering directory `/usr/src/modules/nvidia-kernel'
echo "ROOT_CMD = "
ROOT_CMD = 
/usr/bin/make -w -f debian/rules binary_modules
make[2]: Entering directory `/usr/src/modules/nvidia-kernel'
# select which makefile to use.
rm -f /usr/src/modules/nvidia-kernel/nv/Makefile || true
if [ 6 = 6  ]; then \
             cd /usr/src/modules/nvidia-kernel/nv ; \
             ln -s Makefile.kbuild Makefile ; \
             cd .. ; \
             if [ 0 = 1 ]; then \
                dpatch apply 01_sysfs ; \
                dpatch status 01_sysfs >patch-stamp ; \
                dpatch apply 02_pcialias ; \
                dpatch status 02_pcialias >>patch-stamp ; \
             fi \
        fi
if [  6 = 4  ]; then \
             cd /usr/src/modules/nvidia-kernel/nv ; \
             ln -s Makefile.nvidia Makefile ; \
             cd .. ; \
        fi
#nothing here anymore
touch configure-stamp
if [ -f /usr/src/modules/nvidia-kernel/debian/control.template ]; then \
                cp  /usr/src/modules/nvidia-kernel/debian/control.template /usr/                                                                                                                                   
src/modules/nvidia-kernel/debian/control; \
        fi
dh_testdir
dh_testroot
PATCHLEVEL = 6 
Kernel compiler version : 4.1.1
Detected compiler version : 4.1.1
Using compiler gcc-4.1 version 4.1.1
touch /usr/src/modules/nvidia-kernel/nv/gcc-check
touch /usr/src/modules/nvidia-kernel/nv/cc-sanity-check
## Main Make ##
IGNORE_CC_MISMATCH=1 CC="gcc-4.1"  /usr/bin/make -C /usr/src/modules/nvidia-kern                                                                                                                                   
el/nv -f Makefile SYSSRC=/usr/src/linux   KBUILD_PARAMS="-C /usr/src/linux SUBDI                                                                                                                                   
RS=/usr/src/modules/nvidia-kernel/nv" module;
make[3]: Entering directory `/usr/src/modules/nvidia-kernel/nv'
Your kernel was configured to include rivafb support!

The rivafb driver conflicts with the NVIDIA driver, please
reconfigure your kernel and *disable* rivafb support, then
try installing the NVIDIA kernel module again.

*** Failed rivafb sanity check. Bailing out! ***

make[3]: *** [rivafb-sanity-check] Error 1
make[3]: Leaving directory `/usr/src/modules/nvidia-kernel/nv'
make[2]: *** [build-stamp] Error 2
make[2]: Leaving directory `/usr/src/modules/nvidia-kernel'
make[1]: *** [kdist_image] Error 2
make[1]: Leaving directory `/usr/src/modules/nvidia-kernel'
Module /usr/src/modules/nvidia-kernel failed.
Hit return to Continue
```

And no, I haven't accidently enabled riva in my kernel.

---

### Post by tseliot on 2007-01-07
Try Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

