---
title: "Error: &quot;make: *** No rule to make target `folder'. Stop.&quot;"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by Luciano_Andrade_Re on 2015-01-13
Hi all,

I'am running Ubuntu 12.04 LTS, and I am trying to install the USB/UART driver to work with an FPGA. I downloaded the file for Linux Kernel 2.6.18-3.4.x , and when I do 

$ make

I get this error:
 
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-70-generic-pae'
make[1]: *** No rule to make target `UART/UDriver'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-70-generic-pae'
make: *** [all] Error 2


The Makefile is:

obj-m := vizzini.o

KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD       := $(shell pwd)

EXTRA_CFLAGS    := -DDEBUG=0

all:
    $(MAKE) -C $(KERNELDIR) M=$(PWD)

modules_install:
    $(MAKE) -C $(KERNELDIR) M=$(PWD) modules_install

clean:
    rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions vtty


Any suggestions ?

---

### Post by steeldriver on 2015-01-14
Hello and welcome to the forums

Where did you get the source file? There are lots of references on the web to the vizzini driver for 2.6.x NOT being compatible with 3.x kernels, so I'm surprised you found a version that claims to work on both. If you can provide a link to download it I will try to make time to investigate.

---

### Post by Luciano_Andrade_Re on 2015-01-18
Hello, thank you for the reply.

The source file I downloaded from:

[http://www.exar.com/common/content/default.aspx?id=10296](http://www.exar.com/common/content/default.aspx?id=10296)

That reference is from digilent's Atlys FPGA reference Manual for the Exar USB-UART Bridge (EXAR part number &#8220;XR21V1410&#8221; ) driver. The Atlys manual you can download it from Digilent's web page  ( [http://www.digilentinc.com/Products/Detail.cfm?NavPath=2,400,836&Prod=ATLYS&CFID=7212578&CFTOKEN=19797d11a176df78-91A8D84F-5056-0201-020F5CFE9889695E](http://www.digilentinc.com/Products/Detail.cfm?NavPath=2,400,836&Prod=ATLYS&CFID=7212578&CFTOKEN=19797d11a176df78-91A8D84F-5056-0201-020F5CFE9889695E) )

Regards,
Luciano

---

### Post by steeldriver on 2015-01-18
Hi I followed BOTH "Linux 2.6.18 to 3.4.x" driver links, and the appear to download the same package xr_usb_serial_common_lnx-2.6.18-to-3.4-pak.zip

However the unpacked archive seems to contain a single makefile, whose obj-m is 

```

obj-m := xr_usb_serial_common.o

```

I can't find any reference to vizzini anywhere in the source - can you provide a link to the EXACT download that you used please?

---

### Post by Luciano_Andrade_Re on 2015-01-18
Thay just updated the files (Version 1A, 1/9/2015), the one I downloaded about two weeks ago was from 2013. I checked this new package and I got the same error.

make[1]: Entering directory `/usr/src/linux-headers-3.2.0-70-generic-pae'
make[1]: *** No rule to make target `UART/UART'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-70-generic-pae'
make: *** [all] Error 2


The new Makefile:

obj-m := xr_usb_serial_common.o

KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD       := $(shell pwd)

EXTRA_CFLAGS    := -DDEBUG=0

all:
    $(MAKE) -C $(KERNELDIR) M=$(PWD)

modules_install:
    $(MAKE) -C $(KERNELDIR) M=$(PWD) modules_install

clean:
    rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions vtty

----

On the readme file it says " The source code has been tested on Linux kernels 2.6.18 to 3.4.x.  This may also work with other kernels." 

If you need more information please let me know. Thank you!

---

### Post by steeldriver on 2015-01-18
Well it appears to work for me on 12:04 with the 3.2.0-60-generic 32-bit kernel (at least, it produces a .ko file)

Can you confirm you have the linux-headers-generic package installed?

---

### Post by Luciano_Andrade_Re on 2015-01-18
Its installed:

root@Serena:~# apt-get -f install linux-headers-3.2.0-70-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-70-generic-pae is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Luciano_Andrade_Re on 2015-01-20
I've tried some things that appear to work in other threads with similar issues: installed some uncompressed files of linux-source-3.2.0 (didn't work), updated scripts (didn't work) and I checked with the same version as you did (also with other linux headers), but still I get the same error.

make[1]: Entering directory `/usr/src/linux-headers-3.2.0-60-generic'
make[1]: *** No rule to make target `UART/UART'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-60-generic'
make: *** [all] Error 2

Any idea what might be the problem?

Regards,
Luciano

---

### Post by steeldriver on 2015-01-20
Nope sorry - I'm out of ideas. I actually tried **up**dating my kernel (to 3.2.0-75) but I still can't replicate the error - in fact, I have no idea where the UART/UART target is coming from. I can only guess it's related to a kernel module that I don't have on my system (possibly something you have installed for your particular usb-serial hardware?).

---

### Post by Luciano_Andrade_Re on 2015-01-20
I haven't installed other modules related to the usb-serial hardware. Anyway, I'll try to uninstall everything is not used. 

I'll let you know how it goes, thank you, 
Luciano

---

### Post by Luciano_Andrade_Re on 2015-01-21
It was the name or location of the folder, maybe to large or the spaces in between (that's why the UART/UART target). A new folder on the desktop and worked fine.

Thank you,
Luciano

---

