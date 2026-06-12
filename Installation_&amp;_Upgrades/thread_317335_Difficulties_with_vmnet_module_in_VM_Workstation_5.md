---
title: "Difficulties with vmnet module in VM Workstation 5 Installation"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by moore757 on 2006-12-12
Hello all, 

This is my very first post on this forum, I hope it is a good one.  

I am currently attempting to install vmware Workstation 5 on  Ubuntu 6.06 Dapper.  Essentially I have done everything for the last several years on Fedora Core 4 and finally decideed to make the jump.  I am used to using rpm's to perform installations of more mainstream products such as VMware and am having a few difficulties with my current attempts using the vmware-config.pl installation method.  

This is a clean installation of 6.06 with all initial updates performed(using synaptic)  I made sure to grab the necessary gcc / g++ stuff using. 

> sudo apt-get install build-essential 

and the ncessary C header files using 

> sudo apt-get install linux-headers-`uname -r`

Everything goes very nicely with the installation up until I get to the final stages of the networking configuration where I am getting a rather cryptic error regarding the building of the VMNET module.  Have is a sample of the installation output with the error.

> Do you want to be able to use host-only networking in your virtual machines?
[yes] no

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.15-27-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-386'
  CC [M]  /tmp/vmware-config0/vmnet-only/driver.o
In file included from /tmp/vmware-config0/vmnet-only/vnet.h:14,
                 from /tmp/vmware-config0/vmnet-only/vnetInt.h:10,
                 from /tmp/vmware-config0/vmnet-only/driver.c:40:
/tmp/vmware-config0/vmnet-only/vm_atomic.h:54:5: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmnet-only/vm_oui.h:13,
                 from /tmp/vmware-config0/vmnet-only/vnetInt.h:11,
                 from /tmp/vmware-config0/vmnet-only/driver.c:40:
/tmp/vmware-config0/vmnet-only/vm_basic_asm.h:48:5: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmnet-only/driver.c: In function ‘VNetProcessOwnsPort’:
/tmp/vmware-config0/vmnet-only/driver.c:1698: error: ‘struct files_struct’ has no member named ‘max_fds’
make[2]: *** [/tmp/vmware-config0/vmnet-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27-386'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
 

I have attempted to find any information regarding the driver.c error message within the output, as well as other aspects of the error message and simply cannot find an answer.  I am hoping that with the popularity of VMware and ubuntu somebody else will have encountered this problem.  


thanks,
//matt

---

### Post by celsofaf on 2006-12-16
(please disconsider this post of mine)

---

