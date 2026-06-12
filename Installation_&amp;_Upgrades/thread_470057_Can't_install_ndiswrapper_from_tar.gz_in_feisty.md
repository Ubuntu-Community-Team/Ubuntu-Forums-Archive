---
title: "Can't install ndiswrapper from tar.gz in feisty"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by MightyMouse on 2007-06-10
Dear all,

I have just installed feisty and as usual have no connection to the internet because my wireless adapters are not recognized. Since I don't have a direct cable connection I thought I give it a try to get my wireless card working.

I have a USB Linksys WUSB11 v4.0 802.11b Adapter that used to work with ndiswrapper.
Now the catch, I obviously can't install ndiswrapper with apt-get or Synaptic.
I tried different tar.gz versions, 1.8 and 1.46 but none of them I acn install.

I will post the output of my last attempt with version 1.8 (since I have read that one needs this version due to some issues with Edgy).

I downloaded the tar.gz, then in the folder I stored it (in my home directory) I used tar xvzf ndiswrapper-1.18.tar.gz to unpack.
In the created folder I tried:

make distclean
make
sudo make install


This is the terminal output I get:


anja@anja-maus:~/ndiswrapper/ndiswrapper-1.18$ make distclean
make -C driver clean
make[1]: Entering directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o x86_64_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions
make[1]: Leaving directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
make -C utils clean
make[1]: Entering directory `/home/anja/ndiswrapper/ndiswrapper-1.18/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/home/anja/ndiswrapper/ndiswrapper-1.18/utils'
rm -f *~
rm -fr ndiswrapper-1.18 ndiswrapper-1.18.tar.gz patch-stamp
make -C driver distclean
make[1]: Entering directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o x86_64_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions
rm -f *_exports.h .\#* x86_64_stubs.h
make[1]: Leaving directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
make -C utils distclean
make[1]: Entering directory `/home/anja/ndiswrapper/ndiswrapper-1.18/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/home/anja/ndiswrapper/ndiswrapper-1.18/utils'
rm -f .\#*


anja@anja-maus:~/ndiswrapper/ndiswrapper-1.18$ make
make -C driver
make[1]: Entering directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/anja/ndiswrapper/ndiswrapper-1.18/driver \
                DRIVER_VERSION=1.18
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  LD      /home/anja/ndiswrapper/ndiswrapper-1.18/driver/built-in.o
  CC [M]  /home/anja/ndiswrapper/ndiswrapper-1.18/driver/hal.o
  CC [M]  /home/anja/ndiswrapper/ndiswrapper-1.18/driver/iw_ndis.o
  CC [M]  /home/anja/ndiswrapper/ndiswrapper-1.18/driver/loader.o
  CC [M]  /home/anja/ndiswrapper/ndiswrapper-1.18/driver/misc_funcs.o
  CC [M]  /home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.o
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43:41: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘ndis_init’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43: error: (Each undeclared identifier is reported only once
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43: error: for each function it appears in.)
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘NdisMRegisterInterrupt’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:1860: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘NdisMIndicateReceivePacket’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:2111: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘NdisMTransferDataComplete’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:2381: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
make[3]: *** [/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.o] Error 1
make[2]: *** [_module_/home/anja/ndiswrapper/ndiswrapper-1.18/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
make: *** [all] Error 2


anja@anja-maus:~/ndiswrapper/ndiswrapper-1.18$ sudo make install
make -C driver install
make[1]: Entering directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/anja/ndiswrapper/ndiswrapper-1.18/driver \
                DRIVER_VERSION=1.18
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.o
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43:41: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘ndis_init’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43: error: (Each undeclared identifier is reported only once
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:43: error: for each function it appears in.)
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘NdisMRegisterInterrupt’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:1860: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘NdisMIndicateReceivePacket’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:2111: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c: In function ‘NdisMTransferDataComplete’:
/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.c:2381: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
make[3]: *** [/home/anja/ndiswrapper/ndiswrapper-1.18/driver/ndis.o] Error 1
make[2]: *** [_module_/home/anja/ndiswrapper/ndiswrapper-1.18/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/anja/ndiswrapper/ndiswrapper-1.18/driver'
make: *** [install] Error 2

And thus obviously:

anja@anja-maus:~/ndiswrapper/ndiswrapper-1.18$ ndiswrapper
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
bash: ndiswrapper: command not found


So ndiswrapper is not installed, without it I can most likely not get my wireless working.

Any help would appreciated.

Cheers,
Anja

---

### Post by MightyMouse on 2007-06-12
Solved the problem on my own.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28install%29%7C%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28install%29%7C%28ndiswrapper%29)

For Feisty one needs the ndiswrapper-1.9 debian packages.

Commands to install worked just as mentioned in the documentation.

sudo dpkg -i ndiswrapper-common_*.deb
  sudo dpkg -i ndiswrapper-utils*.deb
  sudo dpkg -i --force-depends ndisgtk_*.deb

Still, when I do 
$ ndiswrapper -v
I get something like version unknown or so, but just ignore that, ndiswrapper works as it should after that.

I still have some problems connecting to the net but I hope to have solved those shortly.
:KS
Cheers, Anja

---

