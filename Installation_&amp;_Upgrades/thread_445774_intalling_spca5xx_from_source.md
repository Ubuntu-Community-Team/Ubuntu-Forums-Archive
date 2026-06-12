---
title: "intalling spca5xx from source"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by peterbug on 2007-05-16
when I try to install I get the following code. I have no idea why it wont install could someone please help?

```
peterbug@peterbug-desktop:~/install/spca5xx-v4l1goodbye$ sudo make
Password:
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/peterbug/install/spca5xx-v4l
1goodbye CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:39:26: error: l
inux/config.h: No such file or directory
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca50x_init_isoc’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:1623: warning:
assignment from incompatible pointer type
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca5xx_open’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning:
implicit declaration of function ‘video_devdata’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2394: warning:
initialization makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning:
implicit declaration of function ‘video_get_drvdata’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2399: warning:
initialization makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca5xx_close’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2489: warning:
initialization makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca5xx_do_ioctl’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:2549: warning:
initialization makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca5xx_ioctl’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3093: warning:
implicit declaration of function ‘video_usercopy’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca5xx_read’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3112: warning:
initialization makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca5xx_mmap’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3211: warning:
initialization makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: At top level:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3263: error: va
riable ‘spca50x_template’ has initializer but incomplete type
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: error: un
known field ‘owner’ specified in initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning:
excess elements in struct initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3264: warning:
(near initialization for ‘spca50x_template’)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: error: un
known field ‘name’ specified in initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning:
excess elements in struct initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3265: warning:
(near initialization for ‘spca50x_template’)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: error: un
known field ‘type’ specified in initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning:
excess elements in struct initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3266: warning:
(near initialization for ‘spca50x_template’)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: error: un
known field ‘hardware’ specified in initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning:
excess elements in struct initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3267: warning:
(near initialization for ‘spca50x_template’)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: error: un
known field ‘fops’ specified in initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning:
excess elements in struct initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3268: warning:
(near initialization for ‘spca50x_template’)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: un
known field ‘release’ specified in initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: error: ‘v
ideo_device_release’ undeclared here (not in a function)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning:
excess elements in struct initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3270: warning:
(near initialization for ‘spca50x_template’)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: error: un
known field ‘minor’ specified in initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning:
excess elements in struct initializer
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3272: warning:
(near initialization for ‘spca50x_template’)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘c
d_to_spca50x’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning:
implicit declaration of function ‘to_video_device’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3340: warning:
initialization makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3341: warning:
return makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca50x_create_sysfs’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:3450: warning:
implicit declaration of function ‘video_device_create_file’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c: In function ‘s
pca5xx_probe’:
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning:
implicit declaration of function ‘video_device_alloc’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5509: warning:
assignment makes pointer from integer without a cast
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: in
valid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: in
valid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5512: error: in
valid application of ‘sizeof’ to incomplete type ‘struct video_device’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5514: error: de                              referencing pointer to incomplete type
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5516: warning:                               implicit declaration of function ‘video_set_drvdata’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: warning:                               implicit declaration of function ‘video_register_device’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: ‘V                              FL_TYPE_GRABBER’ undeclared (first use in this function)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: (E                              ach undeclared identifier is reported only once
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5521: error: fo                              r each function it appears in.)
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5550: error: de                              referencing pointer to incomplete type
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5551: warning:                               implicit declaration of function ‘video_device_release’
/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.c:5553: warning:                               implicit declaration of function ‘video_unregister_device’
make[2]: *** [/home/peterbug/install/spca5xx-v4l1goodbye/drivers/usb/spca5xx.o]                               Error 1
make[1]: *** [_module_/home/peterbug/install/spca5xx-v4l1goodbye] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

```

---

