---
title: "OpenGL Problem in Intel 82915G/GV/910GL Video Card"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by KyleZOA on 2008-09-14
I've been having problems with OpenGL lately with Intrepid. On OpenGL programs (e.g. Google Earth) the screen where the "drawing" is contained, is completely blank. I have installed the python-opengl and the libqt package with no avail.

I tried to install the i915 driver with also no avail, below is the dri.log:

make -C /lib/modules/2.6.27-3-generic/build SUBDIRS=/home/kyle/dripkg/agpgart-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-3-generic'
  CC [M]  /home/kyle/dripkg/agpgart-2.0/backend.o
/home/kyle/dripkg/agpgart-2.0/backend.c:68: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/kyle/dripkg/agpgart-2.0/backend.c:77: error: conflicting types for ‘agp_backend_acquire’
include/linux/agp_backend.h:105: error: previous declaration of ‘agp_backend_acquire’ was here
/home/kyle/dripkg/agpgart-2.0/backend.c:88: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/kyle/dripkg/agpgart-2.0/backend.c:93: error: conflicting types for ‘agp_backend_release’
include/linux/agp_backend.h:106: error: previous declaration of ‘agp_backend_release’ was here
/home/kyle/dripkg/agpgart-2.0/backend.c:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘drm_agp’
/home/kyle/dripkg/agpgart-2.0/backend.c: In function ‘agp_add_bridge’:
/home/kyle/dripkg/agpgart-2.0/backend.c:281: error: implicit declaration of function ‘inter_module_register’
/home/kyle/dripkg/agpgart-2.0/backend.c:281: error: ‘drm_agp’ undeclared (first use in this function)
/home/kyle/dripkg/agpgart-2.0/backend.c:281: error: (Each undeclared identifier is reported only once
/home/kyle/dripkg/agpgart-2.0/backend.c:281: error: for each function it appears in.)
/home/kyle/dripkg/agpgart-2.0/backend.c: In function ‘agp_remove_bridge’:
/home/kyle/dripkg/agpgart-2.0/backend.c:301: error: implicit declaration of function ‘inter_module_unregister’
make[2]: *** [/home/kyle/dripkg/agpgart-2.0/backend.o] Error 1
make[1]: *** [_module_/home/kyle/dripkg/agpgart-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-3-generic'
make: *** [default] Error 2
make -f Makefile.linux DRM_MODULES=gdg.ko modules
make[1]: Entering directory `/home/kyle/dripkg/drm'
make -C /lib/modules/2.6.27-3-generic/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.27-3-generic'
rm: cannot remove `/home/kyle/dripkg/drm/.tmp_versions/CVS': Is a directory
make[2]: *** [crmodverdir] Error 1
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-3-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/kyle/dripkg/drm'
make: *** [gdg.ko] Error 2

From here, I have really no clue on what to do next. OpenGL has worked in Hardy before but not in Intrepid anymore.

Thanks in advance.

---

