---
title: "creative PD1001 webcam"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Misbah Naveed on 2008-02-04
Hi
I am trying to load my webcam "creative PD1001 Ep800 chipset".working on RHEL4 with kernel-2.6.9-42 version.i download the source epcam-src-ubuntu-0[1].7.2.tar.
i perform the following steps:

1. [root@localhost CPD1001]# make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/root/Desktop/CPD1001 modules
make[1]: Entering directory `/usr/src/kernels/2.6.9-42.EL-i686'
  CC [M]  /root/Desktop/CPD1001/drivers/usb/epcam.o
/root/Desktop/CPD1001/drivers/usb/epcam.c:55: warning: static declaration of 'remap_page_range' follows non-static declaration
include/linux/mm.h:776: warning: previous declaration of 'remap_page_range' was here
/root/Desktop/CPD1001/drivers/usb/epcam.c: In function `remap_page_range':
/root/Desktop/CPD1001/drivers/usb/epcam.c:56: warning: implicit declaration of function `remap_pfn_range'
/root/Desktop/CPD1001/drivers/usb/epcam.c: In function `epcam_recv_pict':
/root/Desktop/CPD1001/drivers/usb/epcam.c:263: warning: unused variable `cp'
/root/Desktop/CPD1001/drivers/usb/epcam.c: In function `epcam_start_stream':
/root/Desktop/CPD1001/drivers/usb/epcam.c:470: warning: unused variable `interface'
/root/Desktop/CPD1001/drivers/usb/epcam.c:471: warning: unused variable `endpoint'
  LD [M]  /root/Desktop/CPD1001/epcam.o
  Building modules, stage 2.
  MODPOST
*** Warning: "remap_pfn_range" [/root/Desktop/CPD1001/epcam.ko] undefined!
  LD [M]  /root/Desktop/CPD1001/epcam.ko
make[1]: Leaving directory `/usr/src/kernels/2.6.9-42.EL-i686'

2. Then i did "make install"
3.[root@localhost CPD1001]# modprobe epcam
FATAL: Error inserting epcam (/lib/modules/2.6.9-42.EL/kernel/drivers/usb/media/epcam.ko): Unknown symbol in module, or unknown parameter (see dmesg)

and dmesg  shows a long list some lines are sending
attempt to access beyond end of device
sda1: rw=0, want=19931026, limit=4128642
Buffer I/O error on device sda1, logical block 19931025
attempt to access beyond end of device
sda1: rw=0, want=19931027, limit=4128642
Buffer I/O error on device sda1, logical block 19931026
attempt to access beyond end of device
sda1: rw=0, want=19931028, limit=4128642
Buffer I/O error on device sda1, logical block 19931027
attempt to access beyond end of device
sda1: rw=0, want=19931029, limit=4128642
Buffer I/O error on device sda1, logical block 19931028
attempt to access beyond end of device
sda1: rw=0, want=19931030, limit=4128642
Buffer I/O error on device sda1, logical block 19931029
attempt to access beyond end of device
sda1: rw=0, want=19931031, limit=4128642
Buffer I/O error on device sda1, logical block 19931030
attempt to access beyond end of device
sda1: rw=0, want=19931032, limit=4128642
Buffer I/O error on device sda1, logical block 19931031
attempt to access beyond end of device
sda1: rw=0, want=24125329, limit=4128642
Buffer I/O error on device sda1, logical block 24125328


Kindly tell me what i do now?

---

