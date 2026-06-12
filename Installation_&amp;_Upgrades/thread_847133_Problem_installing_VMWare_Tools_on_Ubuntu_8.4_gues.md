---
title: "Problem installing VMWare Tools on Ubuntu 8.4 guest OS"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by pkto on 2008-07-02
Hi,

My PC is using Window XP.
I'm using VMWare Server Console 1.5.0.build-80187
I have a guess OS on the VMWare Server is Ubuntu 8.4.
I try to install VMWare Tools on Ubuntu 8.4 and had the following problem

> 
root@pkto-Ubuntu:/home/pkto/Desktop/vmware-tools-distrib# vi INSTALL 
root@pkto-Ubuntu:/home/pkto/Desktop/vmware-tools-distrib# ls
bin  doc  etc  FILES  INSTALL  installer  lib  vmware-install.pl
root@pkto-Ubuntu:/home/pkto/Desktop/vmware-tools-distrib# ./vmware-install.pl 
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

The path "/usr/lib/vmware-tools" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

The installation of VMware Tools 1.0.5 build-80187 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] yes


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] /lib/modules/2.6.24-19-generic/build/include

The directory of kernel headers (version 2.6.24-19-generic) does not match your
running kernel (version 2.6.24-16-generic).  Even if the module were to compile
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmhgfs-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config3/vmhgfs-only/cpName.o
In file included from include/linux/string.h:11,
                 from /tmp/vmware-config3/vmhgfs-only/cpName.h:18,
                 from /tmp/vmware-config3/vmhgfs-only/cpName.c:18:
include/linux/types.h:40: error: conflicting types for ‘uintptr_t’
/tmp/vmware-config3/vmhgfs-only/vm_basic_types.h:161: error: previous declaration of ‘uintptr_t’ was here
make[2]: *** [/tmp/vmware-config3/vmhgfs-only/cpName.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmhgfs-only'
Unable to build the vmhgfs module.

The filesystem driver (vmhgfs module) is used only for the shared folder 
feature. The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you wish to have the shared folders feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.

pcnet32                34820  0 
Unloading pcnet32 module

Trying to find a suitable vmxnet module for your running kernel.

None of the pre-built vmxnet modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmxnet module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Extracting the sources of the vmxnet module.

Building the vmxnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config4/vmxnet-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config4/vmxnet-only/vmxnet.o
In file included from /tmp/vmware-config4/vmxnet-only/vmxnet.c:36:
/tmp/vmware-config4/vmxnet-only/vm_basic_types.h:161: error: conflicting types for ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
/tmp/vmware-config4/vmxnet-only/vmxnet.c: In function ‘vmxnet_probe_device’:
/tmp/vmware-config4/vmxnet-only/vmxnet.c:473: error: implicit declaration of function ‘SET_MODULE_OWNER’
/tmp/vmware-config4/vmxnet-only/vmxnet.c: In function ‘vmxnet_open’:
/tmp/vmware-config4/vmxnet-only/vmxnet.c:671: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/tmp/vmware-config4/vmxnet-only/vmxnet.c:671: error: (Each undeclared identifier is reported only once
/tmp/vmware-config4/vmxnet-only/vmxnet.c:671: error: for each function it appears in.)
/tmp/vmware-config4/vmxnet-only/vmxnet.c:671: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/tmp/vmware-config4/vmxnet-only/vmxnet.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmxnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmxnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmxnet-only'
Unable to build the vmxnet module.

The fast network device driver (vmxnet module) is used only for our fast 
networking interface. The rest of the software provided by VMware Tools is 
designed to work independently of this feature.
If you wish to have the fast network driver enabled, you can install the driver
by running vmware-config-tools.pl again after making sure that gcc, binutils, 
make and the kernel sources for your running kernel are installed on your 
machine. These packages are available on your distribution's installation CD.
[ Press Enter key to continue]




Can anyone help?
Thanks,

---

### Post by ezramorris on 2008-09-14
I'm having this problem too with VMware server 1.0.6, Ubuntu 8.10.

Any help would be much appreciated.

---

### Post by ezramorris on 2008-09-16
I tried some solutions using open-vm-tools, but the current version(s) of gcc won't compile them, and there is this one dependency which Ubuntu's version is too old for.

[COLOR="Red"]Edit:[/COLOR] If you want, you can download a pre-made appliance here: [http://chrysaor.info/?page=ubuntu](http://chrysaor.info/?page=ubuntu) . It's the top download.

---

