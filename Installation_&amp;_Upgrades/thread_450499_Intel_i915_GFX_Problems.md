---
title: "Intel i915 GFX Problems"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by Mr Chimp on 2007-05-21
Hello, I am trying to install a new driver for my Intel i915 gfx card. Currently im stuck using a resolution of 640x480!! 

I have downloaded the correct files and have tried to install them but I get the error: 
"The DRI drivers cannot be installed without the latest Kernel modules. Installation will be aborted. See the dri.log file for information on what went wrong"

The dri.log does not really indicate the error.

The laptop is:
Acer Travelmate 280
P4m @ 1.80Ghz
Intel i915 GFX Card (Intel 82845G/GL/GE/PE/GV Controler
Running Feisty Faun

*Edit*

Dri.log - 
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/arran/Desktop/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/arran/Desktop/dripkg/agpgart-2.0/backend.o
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:69: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:110: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for &#8216;agp_backend_acquire&#8217;
include/linux/agp_backend.h:110: error: previous declaration of &#8216;agp_backend_acquire&#8217; was here
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:89: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:111: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for &#8216;agp_backend_release&#8217;
include/linux/agp_backend.h:111: error: previous declaration of &#8216;agp_backend_release&#8217; was here
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:220: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;drm_agp&#8217;
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_add_bridge&#8217;:
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:281: warning: implicit declaration of function &#8216;inter_module_register&#8217;
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:281: error: &#8216;drm_agp&#8217; undeclared (first use in this function)
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c: In function &#8216;agp_remove_bridge&#8217;:
/home/arran/Desktop/dripkg/agpgart-2.0/backend.c:301: warning: implicit declaration of function &#8216;inter_module_unregister&#8217;
make[2]: *** [/home/arran/Desktop/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/arran/Desktop/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/arran/Desktop/dripkg/drm'
+ ln -s Makefile.linux Makefile
make -C /lib/modules/2.6.20-15-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
rm: cannot remove `/home/arran/Desktop/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/arran/Desktop/dripkg/drm'
make: *** [gdg.ko] Error 2

---

### Post by Metacarpal on 2007-05-21
run this in Terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you to specify a driver, select either your new driver from the list, or the i810 driver.  (Don't use the "Intel" driver, as when you close your laptop and reopen it, your screen will stay blank.)

Most of the rest of the questions can be just Entered through.  When you get to the section asking about resolution, make sure you use spacebar to select (*) the resolutions you want to use.  I usually keep mine at 1280x768 widescreen.  When it gives a list of drivers such as vbe, dri, and so on, select everything but Record and V4L.
You'll have to choose resolutions again when you get to Monitor.  Don't choose Simple setup - either go for Medium or (if you really know your monitor's specs) Advanced.

When you're done, restart the X server with a quick Ctrl-Alt-Backspace, or restart the computer entirely.

That should fix you right up.

---

