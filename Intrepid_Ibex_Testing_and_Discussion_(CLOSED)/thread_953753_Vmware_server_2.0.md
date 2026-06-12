---
title: "Vmware server 2.0"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by soxs on 2008-10-20
Hi
I ran into another problem..

V,ware server refuses to build it's vix thingy which interacts with the kernel. This gave me a error while doing a compile via the included config script (see the subfolder bin).

The good thing is, that some guys actually managed to make it work under ubuntu 8.10 beta latest kernel availiable (see launchpad)... so how did they do that and what is requireed to build vmware. I installed the kernel-source, make, binutils, make, checkinsstall, gcc4.3 and gcc4.2
#
Plx help

---

### Post by soxs on 2008-10-20
```
None of the pre-built vsock modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vsock module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Extracting the sources of the vsock module.

Building the vsock module.

Using 2.6.x kernel build system.
make: Gehe in Verzeichnis '/tmp/vmware-config0/vsock-only'
make -C /lib/modules/2.6.27-4-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.27-4-generic'
  CC [M]  /tmp/vmware-config0/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config0/vsock-only/linux/util.o
/tmp/vmware-config0/vsock-only/linux/util.c: In Funktion »VSockVmciLogPkt«:
/tmp/vmware-config0/vsock-only/linux/util.c:157: Warnung: Format ist kein Zeichenkettenliteral, und keine Formatargumente
  CC [M]  /tmp/vmware-config0/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "VMCIDatagram_CreateHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_DestroyHnd" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCI_GetContextID" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
WARNING: "VMCIDatagram_Send" [/tmp/vmware-config0/vsock-only/vsock.ko] undefined!
  CC      /tmp/vmware-config0/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config0/vsock-only/vsock.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.27-4-generic'
cp -f vsock.ko ./../vsock.o
make: Verlasse Verzeichnis '/tmp/vmware-config0/vsock-only'
Unable to make a vsock module that can be loaded in the running kernel:
insmod: error inserting '/tmp/vmware-config0/vsock.o': -1 Unknown symbol in module
There is probably a slight difference in the kernel configuration between the 
set of C header files you specified and your running kernel.  You may want to 
rebuild a kernel based on that directory, or specify another directory.

The VM communication interface socket family is used in conjunction with the VM
communication interface to provide a new communication path among guests and 
host.  The rest of this software provided by VMware Server is designed to work 
independently of this feature.  If you wish to have the VSOCK feature  you can 
install the driver by running vmware-config.pl again after making sure that 
gcc, binutils, make and the kernel sources for your running kernel are 
installed on your machine. These packages are available on your distribution's 
installation CD.
[ Press the Enter key to continue.] 
```

---

