---
title: "VMware doesn't work after upgrade to 8.0"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by aboabo on 2008-04-30
Hi,

I've had vmware installed on my system and working fine for version 7.10. After upgrading to the new version, it promotes to run the 
sudo /usr/bin/vmware-config.pl 
for reconfiguration. However the reconfiguration failed halfway and here is the message

"
None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.24-16-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.24-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:83:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:168: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/x86.h:23,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/x86cpuid.h:383:1: warning: "BIT_MASK" redefined
In file included from include/linux/kernel.h:15,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:11:
include/linux/bitops.h:7:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config1/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:84:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:198: warning: initialisation from incompatible pointer type
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
"

Does anyone know how do I fix this?

Thx in advance

---

### Post by aboabo on 2008-04-30
I think it has something to do with the 2.6.24 kernal but I'm not sure how to fix this.

---

### Post by pfwd.tech on 2008-04-30
> **aboabo said:**
> 
include/linux/poll.h:65: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:198: warning: initialisation from incompatible pointer type
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.
"

Does anyone know how do I fix this?

Thx in advance
Bump Has any one solved this?

---

### Post by ubnewbie2 on 2008-04-30
I am getting the same thing.  I think there are some patches, but the one I had recommended to me, won't install - see my thread here

[http://ubuntuforums.org/showthread.php?t=775499](http://ubuntuforums.org/showthread.php?t=775499)

---

### Post by sultanoswing on 2008-04-30
> **pfwd.tech said:**
> Bump Has any one solved this?

Worked a charm for me:

[http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29](http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29)

---

### Post by pfwd.tech on 2008-04-30
thanks for the replies. I will try the patches in the am and let you know

---

### Post by ubnewbie2 on 2008-04-30
> **sultanoswing said:**
> Worked a charm for me:

[http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29](http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29)

I have vmware player, not server, and that patch refuses to install as my version is too new (Unknown VMware version 4 is installed. This installer supports only version 2 
and 3.)

---

### Post by gotlinuxed on 2008-05-26
aboabo, I had the same problems as you, just got it working. Posted the fix as a new top level thread:
[http://ubuntuforums.org/showthread.php?p=5045735#post5045735](http://ubuntuforums.org/showthread.php?p=5045735#post5045735)
Hope it works for you.

---

