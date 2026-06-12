---
title: "Installing ndiswrapper1.55"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by RaDeuX on 2009-11-19
So my Dell Inspiron 9100 comes with a Broadcom chipset wireless card, so I need to install ndiswrapper. However, each time I uncompress the file and do "make distclean", it gives me a module 2 error. I'm not sure why. I did everything exactly the same way as this tutorial mentions: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

---

### Post by RaDeuX on 2009-11-19
Even "make" without "distclean" doesn't work...

---

### Post by RaDeuX on 2009-11-21
> 
t@DI9100:/home/radeux/Apps/ndiswrapper-1.55# make
make -C driver
make[1]: Entering directory `/home/radeux/Apps/ndiswrapper-1.55/driver'
make -C /usr/src/linux-headers-2.6.22-14-generic M=/home/radeux/Apps/ndiswrapper-1.55/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  LD      /home/radeux/Apps/ndiswrapper-1.55/driver/built-in.o
  MKEXPORT /home/radeux/Apps/ndiswrapper-1.55/driver/crt_exports.h
  MKEXPORT /home/radeux/Apps/ndiswrapper-1.55/driver/hal_exports.h
  MKEXPORT /home/radeux/Apps/ndiswrapper-1.55/driver/ndis_exports.h
  MKEXPORT /home/radeux/Apps/ndiswrapper-1.55/driver/ntoskernel_exports.h
  MKEXPORT /home/radeux/Apps/ndiswrapper-1.55/driver/ntoskernel_io_exports.h
  MKEXPORT /home/radeux/Apps/ndiswrapper-1.55/driver/rtl_exports.h
  MKEXPORT /home/radeux/Apps/ndiswrapper-1.55/driver/usb_exports.h
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/crt.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/hal.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/iw_ndis.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/loader.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/ndis.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/ntoskernel.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/ntoskernel_io.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/pe_linker.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/pnp.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/proc.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/rtl.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/wrapmem.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/wrapndis.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/wrapper.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/usb.o
  CC [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/divdi3.o
  LD [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/radeux/Apps/ndiswrapper-1.55/driver/ndiswrapper.mod.o
  LD [M]  /home/radeux/Apps/ndiswrapper-1.55/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[1]: Leaving directory `/home/radeux/Apps/ndiswrapper-1.55/driver'
make -C utils
make[1]: Entering directory `/home/radeux/Apps/ndiswrapper-1.55/utils'
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.3/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:28: error: expected specifier-qualifier-list before &#8218;Äòsize_t&#8218;Äô
loadndisdriver.c: In function &#8218;Äòload_file&#8218;Äô:
loadndisdriver.c:67: error: &#8218;Äòsize_t&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8218;Äò;&#8218;Äô before &#8218;Äòsize&#8218;Äô
loadndisdriver.c:68: error: &#8218;ÄòNULL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8218;Äòstatbuf&#8218;Äô isn&#8218;Äôt known
loadndisdriver.c:71: warning: implicit declaration of function &#8218;Äòbasename&#8218;Äô
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8218;Äòopen&#8218;Äô
loadndisdriver.c:73: error: &#8218;ÄòO_RDONLY&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8218;Äòsyslog&#8218;Äô
loadndisdriver.c:75: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:75: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8218;Äòstrerror&#8218;Äô
loadndisdriver.c:75: error: &#8218;Äòerrno&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:76: error: &#8218;ÄòEINVAL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8218;Äòfstat&#8218;Äô
loadndisdriver.c:81: warning: implicit declaration of function &#8218;Äòclose&#8218;Äô
loadndisdriver.c:84: error: &#8218;Äòsize&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8218;Äòmmap&#8218;Äô
loadndisdriver.c:86: error: &#8218;ÄòPROT_READ&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:86: error: &#8218;ÄòMAP_PRIVATE&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8218;ÄòMAP_FAILED&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8218;Äòstrncpy&#8218;Äô
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8218;Äòstrncpy&#8218;Äô
loadndisdriver.c:95: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòsize&#8218;Äô
loadndisdriver.c:96: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòdata&#8218;Äô
loadndisdriver.c:69: warning: unused variable &#8218;Äòstatbuf&#8218;Äô
loadndisdriver.c: In function &#8218;Äòparse_setting_line&#8218;Äô:
loadndisdriver.c:109: warning: implicit declaration of function &#8218;Äòisspace&#8218;Äô
loadndisdriver.c:115: warning: implicit declaration of function &#8218;Äòstrchr&#8218;Äô
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8218;Äòstrchr&#8218;Äô
loadndisdriver.c:115: error: &#8218;ÄòNULL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:117: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:117: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:118: error: &#8218;ÄòEINVAL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8218;Äòstrlen&#8218;Äô
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8218;Äòstrlen&#8218;Äô
loadndisdriver.c: In function &#8218;Äòread_conf_file&#8218;Äô:
loadndisdriver.c:150: error: storage size of &#8218;Äòstatbuf&#8218;Äô isn&#8218;Äôt known
loadndisdriver.c:151: error: &#8218;ÄòFILE&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:151: error: &#8218;Äòconfig&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8218;Äòlstat&#8218;Äô
loadndisdriver.c:158: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:158: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:158: error: &#8218;Äòerrno&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:160: error: &#8218;ÄòEINVAL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:163: warning: implicit declaration of function &#8218;Äòsscanf&#8218;Äô
loadndisdriver.c:163: warning: incompatible implicit declaration of built-in function &#8218;Äòsscanf&#8218;Äô
loadndisdriver.c:178: warning: implicit declaration of function &#8218;Äòfopen&#8218;Äô
loadndisdriver.c:178: error: &#8218;ÄòNULL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8218;Äòfgets&#8218;Äô
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8218;Äòstrncpy&#8218;Äô
loadndisdriver.c:205: warning: implicit declaration of function &#8218;Äòfclose&#8218;Äô
loadndisdriver.c:150: warning: unused variable &#8218;Äòstatbuf&#8218;Äô
loadndisdriver.c: In function &#8218;Äòload_bin_file&#8218;Äô:
loadndisdriver.c:217: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:217: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:219: warning: implicit declaration of function &#8218;Äòtolower&#8218;Äô
loadndisdriver.c:221: warning: implicit declaration of function &#8218;Äòchdir&#8218;Äô
loadndisdriver.c:222: error: &#8218;Äòerrno&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:224: error: &#8218;ÄòEINVAL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:230: warning: incompatible implicit declaration of built-in function &#8218;Äòstrncpy&#8218;Äô
loadndisdriver.c:232: warning: implicit declaration of function &#8218;Äòioctl&#8218;Äô
loadndisdriver.c:232: warning: implicit declaration of function &#8218;Äò_IOW&#8218;Äô
loadndisdriver.c:232: error: expected expression before &#8218;Äòstruct&#8218;Äô
loadndisdriver.c: In function &#8218;Äòload_driver&#8218;Äô:
loadndisdriver.c:249: error: &#8218;ÄòDIR&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:249: error: &#8218;Äòdriver_dir&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:251: error: &#8218;ÄòNULL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:255: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:255: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:257: error: &#8218;Äòerrno&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:259: error: &#8218;ÄòEINVAL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:261: warning: implicit declaration of function &#8218;Äòopendir&#8218;Äô
loadndisdriver.c:267: warning: implicit declaration of function &#8218;Äòmalloc&#8218;Äô
loadndisdriver.c:267: warning: incompatible implicit declaration of built-in function &#8218;Äòmalloc&#8218;Äô
loadndisdriver.c:271: warning: implicit declaration of function &#8218;Äòmemset&#8218;Äô
loadndisdriver.c:271: warning: incompatible implicit declaration of built-in function &#8218;Äòmemset&#8218;Äô
loadndisdriver.c:272: warning: incompatible implicit declaration of built-in function &#8218;Äòstrncpy&#8218;Äô
loadndisdriver.c:280: warning: implicit declaration of function &#8218;Äòreaddir&#8218;Äô
loadndisdriver.c:280: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:282: error: storage size of &#8218;Äòstatbuf&#8218;Äô isn&#8218;Äôt known
loadndisdriver.c:284: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: warning: implicit declaration of function &#8218;Äòstat&#8218;Äô
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:288: warning: implicit declaration of function &#8218;ÄòS_ISREG&#8218;Äô
loadndisdriver.c:289: error: dereferencing pointer to incomplete type
loadndisdriver.c:294: warning: incompatible implicit declaration of built-in function &#8218;Äòstrlen&#8218;Äô
loadndisdriver.c:294: error: dereferencing pointer to incomplete type
loadndisdriver.c:296: warning: implicit declaration of function &#8218;Äòstrcasecmp&#8218;Äô
loadndisdriver.c:296: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:303: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:311: error: dereferencing pointer to incomplete type
loadndisdriver.c:312: error: dereferencing pointer to incomplete type
loadndisdriver.c:313: warning: implicit declaration of function &#8218;Äòstrcpy&#8218;Äô
loadndisdriver.c:313: warning: incompatible implicit declaration of built-in function &#8218;Äòstrcpy&#8218;Äô
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:317: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòsize&#8218;Äô
loadndisdriver.c:318: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòdata&#8218;Äô
loadndisdriver.c:321: error: dereferencing pointer to incomplete type
loadndisdriver.c:282: warning: unused variable &#8218;Äòstatbuf&#8218;Äô
loadndisdriver.c:344: error: expected expression before &#8218;Äòstruct&#8218;Äô
loadndisdriver.c:346: warning: implicit declaration of function &#8218;Äòclosedir&#8218;Äô
loadndisdriver.c:348: warning: implicit declaration of function &#8218;Äòfree&#8218;Äô
loadndisdriver.c:355: warning: implicit declaration of function &#8218;Äòmunmap&#8218;Äô
loadndisdriver.c:355: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòdata&#8218;Äô
loadndisdriver.c:355: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòsize&#8218;Äô
loadndisdriver.c:357: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòdata&#8218;Äô
loadndisdriver.c:357: error: &#8218;Äòstruct load_driver_file&#8218;Äô has no member named &#8218;Äòsize&#8218;Äô
loadndisdriver.c: In function &#8218;Äòget_device&#8218;Äô:
loadndisdriver.c:367: error: storage size of &#8218;Äòstatbuf&#8218;Äô isn&#8218;Äôt known
loadndisdriver.c:370: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:370: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:373: error: &#8218;Äòerrno&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:374: error: &#8218;ÄòEINVAL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:376: warning: implicit declaration of function &#8218;Äòsnprintf&#8218;Äô
loadndisdriver.c:376: warning: incompatible implicit declaration of built-in function &#8218;Äòsnprintf&#8218;Äô
loadndisdriver.c:407: warning: incompatible implicit declaration of built-in function &#8218;Äòstrncpy&#8218;Äô
loadndisdriver.c:367: warning: unused variable &#8218;Äòstatbuf&#8218;Äô
loadndisdriver.c: In function &#8218;Äòload_device&#8218;Äô:
loadndisdriver.c:419: error: &#8218;ÄòDIR&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:419: error: &#8218;Äòdir&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:423: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:423: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:424: warning: incompatible implicit declaration of built-in function &#8218;Äòmemset&#8218;Äô
loadndisdriver.c:426: error: &#8218;Äòerrno&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:427: error: &#8218;ÄòEINVAL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:429: error: &#8218;ÄòNULL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:434: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:435: error: dereferencing pointer to incomplete type
loadndisdriver.c:436: error: dereferencing pointer to incomplete type
loadndisdriver.c:439: error: dereferencing pointer to incomplete type
loadndisdriver.c:447: error: expected expression before &#8218;Äòstruct&#8218;Äô
loadndisdriver.c: In function &#8218;Äòget_ioctl_device&#8218;Äô:
loadndisdriver.c:464: error: &#8218;ÄòFILE&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:464: error: &#8218;Äòproc_misc&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:472: warning: implicit declaration of function &#8218;Äòstrstr&#8218;Äô
loadndisdriver.c:472: warning: incompatible implicit declaration of built-in function &#8218;Äòstrstr&#8218;Äô
loadndisdriver.c:473: warning: implicit declaration of function &#8218;Äòstrtol&#8218;Äô
loadndisdriver.c:473: error: &#8218;ÄòNULL&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:483: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:483: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:488: warning: implicit declaration of function &#8218;Äòunlink&#8218;Äô
loadndisdriver.c:489: warning: implicit declaration of function &#8218;Äòmknod&#8218;Äô
loadndisdriver.c:489: error: &#8218;ÄòS_IFCHR&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:489: error: &#8218;ÄòMISC_MAJOR&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:490: error: &#8218;Äòerrno&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:495: error: &#8218;ÄòO_RDONLY&#8218;Äô undeclared (first use in this function)
loadndisdriver.c: In function &#8218;Äòmain&#8218;Äô:
loadndisdriver.c:511: warning: implicit declaration of function &#8218;Äòopenlog&#8218;Äô
loadndisdriver.c:511: error: &#8218;ÄòLOG_PERROR&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:511: error: &#8218;ÄòLOG_CONS&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:511: error: &#8218;ÄòLOG_KERN&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:511: error: &#8218;ÄòLOG_DEBUG&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:513: error: &#8218;ÄòLOG_INFO&#8218;Äô undeclared (first use in this function)
loadndisdriver.c:515: warning: implicit declaration of function &#8218;Äòstrncmp&#8218;Äô
loadndisdriver.c:517: warning: implicit declaration of function &#8218;Äòprintf&#8218;Äô
loadndisdriver.c:517: warning: incompatible implicit declaration of built-in function &#8218;Äòprintf&#8218;Äô
loadndisdriver.c:527: warning: implicit declaration of function &#8218;Äòatoi&#8218;Äô
loadndisdriver.c:542: warning: implicit declaration of function &#8218;Äòatof&#8218;Äô
loadndisdriver.c:549: warning: implicit declaration of function &#8218;Äòstrcmp&#8218;Äô
loadndisdriver.c:556: warning: incompatible implicit declaration of built-in function &#8218;Äòsscanf&#8218;Äô
loadndisdriver.c:590: warning: implicit declaration of function &#8218;Äòcloselog&#8218;Äô
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/home/radeux/Apps/ndiswrapper-1.55/utils'
make: *** [all] Error 2
root@DI9100:/home/radeux/Apps/ndiswrapper-1.55# 





That's the error message I got...

---

