---
title: "Problems Installing VMware"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by jm952370 on 2010-01-13
I am having issues installing vmware on my ubuntu server 8.04

i am following the guide [http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

i have updated the linux headers using apt-get install linux-headers-server

i then change dir to my vmware and attempt to install vmware.pl and get the error

WARNING: Couldn't open directory /lib/modules/2.6.28.4-xxxx-std-ipv4-32: No such file or directory
FATAL: Could not open /lib/modules/2.6.28.4-xxxx-std-ipv4-32/modules.dep.temp for writing: No such file or directory
Unable to open kernel module dependency file
.Execution aborted.


anyone know what this means

thanks

---

### Post by joeinbend on 2010-01-15
We'll need some more info to help out, but off the bat here's a couple things:

install the build essential package:
sudo apt-get install build-essential

when you run the install-vmware.pl, are you using:
sudo ./install-vmware.pl

You dont say in your post, but I assume you are probably installing VMware Server 2.0.x?

---

### Post by YQ002lc2 on 2010-01-30
I have the same problem installing VMware Server 2.0.2

The installer asks where my linux headers are installed and says that it needs to configure itself to work with my present kernel.

Then, I accept the defaults and get the following message:

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.31-17-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:31:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:99:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:101:
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_basic_asm.h:46,
                 from /tmp/vmware-config1/vmmon-only/./include/rateconv.h:45,
                 from /tmp/vmware-config1/vmmon-only/./include/modulecall.h:40,
                 from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:101:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:62:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:177:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:346:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_basic_asm_x86.h:453:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./include/vm_asm.h:43,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:103:
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config1/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:119:
/tmp/vmware-config1/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriverSyncCallOnEachCPU’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1423: error: too many arguments to function ‘smp_call_function’
/tmp/vmware-config1/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1987: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1988: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1989: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:1990: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config1/vmmon-only/linux/driver.c:2007: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

---

### Post by joeinbend on 2010-01-31
Same problem I had. See the link below, this fixed the issue for me and many others as well!
[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

---

