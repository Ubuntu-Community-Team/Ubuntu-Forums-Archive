---
title: "Error in GSPCA-SOURCE"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by nascimento on 2008-07-22
Hello guys!

I'm getting a buggy error when trying to compile my gspca-source for my webcam.

It exits with an CFLAGS error in my Ubuntu "Hardy".
I'm Quoting the error output when trying to compile:

> /gspca# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/src/modules/gspca/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
/gspca#

After that - I've assumed that was some mistake about the C compiler and some "old way" of using the Makefile. So I edit the line in Makefile using the tip that this weird output give me just like that:

```
Old way in Makefile:  CFLAGS += $(DEFINES)
```

Changed to:

```
New way in Makefile: EXTRA_CFLAGS += $(DEFINES)
```

Well  it seems that work just fine... but then...:(... another crash... and this one give me several erros about functions and other stuff. Of course that I cause that by changing that CFLAG, but... what AM I supose to do?:confused: 

I'm a little stuck in here .. can anyone help a little bit?

Thnkx in advance!


New error after EXTRA_CFLAGS:

> 
/gspca# make
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/modules/gspca CC=cc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /usr/src/modules/gspca/gspca_core.o
/usr/src/modules/gspca/gspca_core.c:2567: error: unknown field ‘hardware’ specified in initializer
/usr/src/modules/gspca/gspca_core.c: In function ‘cd_to_spca50x’:
/usr/src/modules/gspca/gspca_core.c:2616: warning: initialization from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c: In function ‘spca50x_create_sysfs’:
/usr/src/modules/gspca/gspca_core.c:2655: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2657: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2659: warning: passing argument 2 of ‘video_device_create_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2665: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2667: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
/usr/src/modules/gspca/gspca_core.c:2669: warning: passing argument 2 of ‘video_device_remove_file’ from incompatible pointer type
make[2]: *** [/usr/src/modules/gspca/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/modules/gspca] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2
/gspca# make

---

### Post by nascimento on 2008-07-22
No one?

=(

---

### Post by themightychris on 2008-09-12
I've run into the same problems, anyone know where to go from here?

---

### Post by loell on 2008-09-12
well, you really don't have to compile. AFAIK its already installed by default and the module will only be loaded if it detects an spca compatible webcam.

---

### Post by ucaka on 2008-10-08
[https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/218554](https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/218554)

---

