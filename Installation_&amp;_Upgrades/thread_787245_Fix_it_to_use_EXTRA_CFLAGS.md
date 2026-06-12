---
title: "Fix it to use EXTRA CFLAGS"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2008-05-08
I'm trying to compile a driver I keep getting errors about CFLAGS was changed Fix it to use EXTRA CFLAGS the make file looks like this 

#***************************************************************************
# Makefile to build Driver executable
#***************************************************************************

PWD	:= $(shell pwd)
INCLUDES = -I $(KERNEL_SOURCE_PATH)/include -I$(PWD)/../inc
 #if no kernel source path was specified, correct INCLUDES to reflect that
ifeq ($(KERNEL_SOURCE_PATH),)
     INCLUDES = -I /lib/modules/`uname -r`/build/include -I ../inc
endif
CFLAGS += $(PSTN_DEF) -Wall -O $(INCLUDES) -fno-common -DTARGET_CATAWBA

DRIVER_OBJS = coredrv.o clmmain.o rts.o task.o uart.o wwh_dflt.o locks.o \
		softserial_io.o softserial_ioctl.o softserial.o
537_OBJS = $(DRIVER_OBJS) afedsp_int.o

clean:
	rm -f *.ko *.o *~ core

537core_26:
	$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

537core:  $(537_OBJS)
	strip --strip-debug 537core.lib
	$(LD) -r $(537_OBJS) 537core.lib -o Intel537.o

KDIR	:= /lib/modules/$(shell uname -r)/build

obj-m := Intel537.o

Intel537-objs := $(537_OBJS) 537core.lib

_________________________________________________________________________

Any ideas?

---

### Post by smo0th on 2011-12-24
change

CFLAGS += $(PSTN_DEF) -Wall -O $(INCLUDES) -fno-common -DTARGET_CATAWBA

to

EXTRA_CFLAGS += $(PSTN_DEF) -Wall -O $(INCLUDES) -fno-common -DTARGET_CATAWBA

and try ;o

you could use something like this:
sed -i 's/^CFLAGS/EXTRA_CFLAGS/' Makefile

it worked for me :)

---

