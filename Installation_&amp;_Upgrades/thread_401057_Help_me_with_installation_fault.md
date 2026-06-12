---
title: "Help me with installation fault"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Mr. Eddy on 2007-04-04
Hi,

I want to install my usr5416 wireless turbo PCI adapter. it uses the ACX 111 chipset. To do that I followed post #6 of this thread [:http://ubuntuforums.org/showthread.php?t=189509&highlight=usr+5416]("http://ubuntuforums.org/showthread.php?t=189509&highlight=usr+5416")

In the installation proces a .deb package is automatically downloaded and starts to install. But I get an error in the installation.

this is my DLDRconfig-buildlog:

```
/lib/modules/2.6.20-13-generic/build/include/net/iw_handler.h:200:56: error: linux/wireless.h: No such file or directory
/lib/modules/2.6.20-13-generic/build/include/net/iw_handler.h:201:28: error: linux/if_ether.h: No such file or directory
(cd /lib/modules/2.6.20-13-generic/build && make "DLDR_KERNELSRC=/lib/modules/2.6.20-13-generic/build" "M=/usr/lib/driverloader/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
/lib/modules/2.6.20-13-generic/build/include/net/iw_handler.h:200:56: error: linux/wireless.h: No such file or directory
/lib/modules/2.6.20-13-generic/build/include/net/iw_handler.h:201:28: error: linux/if_ether.h: No such file or directory
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.20-13-generic/build/.tmp_versions/driverloader.mod Modules.symvers
(cd /lib/modules/2.6.20-13-generic/build && make "DLDR_KERNELSRC=/lib/modules/2.6.20-13-generic/build" "M=/usr/lib/driverloader/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-generic'
/lib/modules/2.6.20-13-generic/build/include/net/iw_handler.h:200:56: error: linux/wireless.h: No such file or directory
/lib/modules/2.6.20-13-generic/build/include/net/iw_handler.h:201:28: error: linux/if_ether.h: No such file or directory
  CC [M]  /usr/lib/driverloader/modules/dldrmod.o
  CC [M]  /usr/lib/driverloader/modules/dldrpci.o
  CC [M]  /usr/lib/driverloader/modules/dldrusb.o
  CC [M]  /usr/lib/driverloader/modules/osusb.o
  CC [M]  /usr/lib/driverloader/modules/GPL/netndis.o
  CC [M]  /usr/lib/driverloader/modules/osservices.o
  CC [M]  /usr/lib/driverloader/modules/osstdio.o
  CC [M]  /usr/lib/driverloader/modules/osresour.o
  CC [M]  /usr/lib/driverloader/modules/osstring.o
  CC [M]  /usr/lib/driverloader/modules/osmemory.o
  CC [M]  /usr/lib/driverloader/modules/GPL/divdi3.o
/usr/lib/driverloader/modules/GPL/divdi3.c:28:20: error: endian.h: No such file or directory
/usr/lib/driverloader/modules/GPL/divdi3.c:29:20: error: stdlib.h: No such file or directory
/usr/lib/driverloader/modules/GPL/divdi3.c:30:27: error: bits/wordsize.h: No such file or directory
/usr/lib/driverloader/modules/GPL/divdi3.c:32:5: warning: "__WORDSIZE" is not defined
/usr/lib/driverloader/modules/GPL/divdi3.c:33:2: error: #error This is for 32-bit targets only
/usr/lib/driverloader/modules/GPL/divdi3.c:51:5: warning: "__BYTE_ORDER" is not defined
/usr/lib/driverloader/modules/GPL/divdi3.c:51:21: warning: "__BIG_ENDIAN" is not defined
/usr/lib/driverloader/modules/GPL/divdi3.c: In function '__divdi3':
/usr/lib/driverloader/modules/GPL/divdi3.c:294: error: 'NULL' undeclared (first use in this function)
/usr/lib/driverloader/modules/GPL/divdi3.c:294: error: (Each undeclared identifier is reported only once
/usr/lib/driverloader/modules/GPL/divdi3.c:294: error: for each function it appears in.)
/usr/lib/driverloader/modules/GPL/divdi3.c: In function '__udivdi3':
/usr/lib/driverloader/modules/GPL/divdi3.c:327: error: 'NULL' undeclared (first use in this function)
make[2]: *** [/usr/lib/driverloader/modules/GPL/divdi3.o] Error 1
make[1]: *** [_module_/usr/lib/driverloader/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-generic'
make: *** [all] Error 2
```

can someone explain what goes wrong in the installation process?

Note: I use feisty

thanks

Edit: It appears my wireless should be supported in feisty, so I do not need toinstall the drivers manually. My wireless isn't working because of a mallfunction of the driver in feisty. This threath is not relevant enymore.

---

