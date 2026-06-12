---
title: "problem compiling cpia2"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by herrodagripa on 2007-12-24
hi
I am a complete beginner. Can anyone tell me in plain English what I am required to do here:

Compiling:
	----------
	As root, do a make install.  This will compile and install the modules
into the media/video directory in the module tree. For 2.4 kernels, use
Makefile_2.4 (aka do make -f Makefile_2.4 install).

thanks.
herrodagripa

---

### Post by lgambett on 2007-12-24
"as root, do a make install" means;
1) open a Terminal on the directory where you copied the software to be compiled
2) give the command
sudo make install

---

### Post by herrodagripa on 2007-12-24
thanks.

I tried that but now have error messages:

john@john-desktop:~/Desktop/cpia2_driver-2.0$ sudo make install
[sudo] password for john:
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/john/Desktop/cpia2_driver-2.0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.o
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:33:26: error: linux/config.h: No such file or directory
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_open’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:280: warning: implicit declaration of function ‘video_devdata’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:280: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:281: warning: implicit declaration of function ‘video_get_drvdata’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:281: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_close’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:352: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:353: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:390: warning: implicit declaration of function ‘video_unregister_device’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_v4l_read’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:408: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:409: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_v4l_poll’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:435: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:436: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_do_ioctl’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:1835: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:1836: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_ioctl’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2136: warning: implicit declaration of function ‘video_usercopy’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_mmap’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2147: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2148: warning: initialisation makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: At top level:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2223: error: variable ‘cpia2_template’ has initialiser but incomplete type
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2225: error: unknown field ‘owner’ specified in initializer
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2225: warning: excess elements in struct initialiser
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2225: warning: (near initialisation for ‘cpia2_template’)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2226: error: unknown field ‘name’ specified in initializer
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2226: warning: excess elements in struct initialiser
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2226: warning: (near initialisation for ‘cpia2_template’)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2227: error: unknown field ‘type’ specified in initializer
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2227: warning: excess elements in struct initialiser
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2227: warning: (near initialisation for ‘cpia2_template’)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2232: error: unknown field ‘hardware’ specified in initializer
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2232: warning: excess elements in struct initialiser
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2232: warning: (near initialisation for ‘cpia2_template’)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2233: error: unknown field ‘minor’ specified in initializer
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2233: warning: excess elements in struct initialiser
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2233: warning: (near initialisation for ‘cpia2_template’)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2234: error: unknown field ‘fops’ specified in initializer
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2234: warning: excess elements in struct initialiser
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2234: warning: (near initialisation for ‘cpia2_template’)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2235: error: unknown field ‘release’ specified in initializer
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2235: error: ‘video_device_release’ undeclared here (not in a function)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2235: warning: excess elements in struct initialiser
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2235: warning: (near initialisation for ‘cpia2_template’)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_register_camera’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2245: warning: implicit declaration of function ‘video_device_alloc’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2245: warning: assignment makes pointer from integer without a cast
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2249: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2249: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2249: error: invalid application of ‘sizeof’ to incomplete type ‘struct video_device’ 
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2250: warning: implicit declaration of function ‘video_set_drvdata’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2256: warning: implicit declaration of function ‘video_register_device’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2256: error: ‘VFL_TYPE_GRABBER’ undeclared (first use in this function)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2256: error: (Each undeclared identifier is reported only once
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2256: error: for each function it appears in.)
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2258: warning: implicit declaration of function ‘video_device_release’
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c: In function ‘cpia2_unregister_camera’:
/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.c:2275: error: dereferencing pointer to incomplete type
make[2]: *** [/home/john/Desktop/cpia2_driver-2.0/cpia2_v4l.o] Error 1
make[1]: *** [_module_/home/john/Desktop/cpia2_driver-2.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
john@john-desktop:~/Desktop/cpia2_driver-2.0$ 
john@john-desktop:~/Desktop/cpia2_driver-2.0$ 

What's wrong?

herrodagripa

---

