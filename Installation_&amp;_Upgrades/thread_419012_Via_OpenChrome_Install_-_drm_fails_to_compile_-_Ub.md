---
title: "Via OpenChrome Install - drm fails to compile - Ubuntu 7.04 Fiesty Fawn"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by MayOne.Net on 2007-04-22
I've successfully compiled OpenChrome driver for my Gateway MX3210 laptop with a VIA VN800 video using a combination of the debian guide located here (gives a good list of things to install before you can compile): 
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Debian](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code+on+Debian)

and the Ubutunu OpenChrome Docs located here:
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

While this allowed me to increase the resolution, and appears to be working for 2d, when I run "glxinfo | grep render" I get the following error:

X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  19
  Current serial number in output stream:  19

So, I  installed the libdrm as per the Ubuntu docs w/out problem, and when I tried to make using  "sudo make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via"

I get the following error

make -C /lib/modules/2.6.20-15-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/shad/stuff/drm/linux-core/drm_compat.o
/home/shad/stuff/drm/linux-core/drm_compat.c:190: error: static declaration of ‘vm_insert_pfn’ follows non-static declaration
include/linux/mm.h:1126: error: previous declaration of ‘vm_insert_pfn’ was here
make[2]: *** [/home/shad/stuff/drm/linux-core/drm_compat.o] Error 1
make[1]: *** [_module_/home/shad/stuff/drm/linux-core] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2

While I can live with 2d only, I would prefer 3d.  Also if I have to live with 2d, how do I uninstall the libdrm, as it appears to be slowing down my boot & shutdown times.  

FYI - was unable to use automake-1.9 as I could only apt-get 1.10.  Would this be part of the problem?  If so, how do I get 1.9?

Thanks for any help.

---

