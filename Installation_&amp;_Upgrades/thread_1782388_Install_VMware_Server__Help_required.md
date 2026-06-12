---
title: "Install VMware Server : Help required"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by f17th on 2011-06-14
Hi 

I've been trying to get a copy of VM Ware Server installed on my Ubuntu machine. I tried the Version 2 with the patch available but seeing as I couldn't access the management console due to Firefox I had to abandon that idea.
Can anyone help me out with installing Version 1.10?

I've unzipped the package and run the command to install 
sudo ./vmware-install.pl

However the install bombs out part way though 

Thanks for taking a look 

Gav

Here's the tail of the error :

> 
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:226:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:230:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:298:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:304:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_And’:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:402:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Or’:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:489:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Xor’:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:576:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Add’:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:665:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Sub’:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:748:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:750:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Inc’:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:831:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:833:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: In function ‘Atomic_Dec’:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:912:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:914:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h: At top level:
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1073:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1077:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_atomic.h:1454:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.h:20:0,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:49:
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config0/vmmon-only/./include/compat_wait.h:60:13: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:72:13: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_basic_asm.h:32:0,
                 from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:25,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:52:
/tmp/vmware-config0/vmmon-only/./include/vm_basic_asm_x86.h:48:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_basic_asm_x86.h:109:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_basic_asm_x86.h:278:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_basic_asm_x86.h:385:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/./include/vm_asm.h:30:0,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:52:
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:430:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:676:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config0/vmmon-only/./include/vm_asm_x86.h:716:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config0/vmmon-only/linux/vmhost.h:13:0,
                 from /tmp/vmware-config0/vmmon-only/linux/driver.c:71:
/tmp/vmware-config0/vmmon-only/./include/compat_semaphore.h:5:27: fatal error: asm/semaphore.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


---

### Post by f17th on 2011-06-15
Hi Again

Sorry I want to get a working solution up as soon as possible.
I've gone back and re installed VM Ware Server 2 on my Ubuntu 11.04 machine as this might be the quickest method.

I still can't get access to the console screen using any version of firefox. Found this ftp site with previous releases : [ftp://ftp.mozilla.org/pub/firefox/releases/](ftp://ftp.mozilla.org/pub/firefox/releases/)

I can get the plug-in installed on firefox but when clicking on the console it doesn't launch the pop up. 
I am going to try IE6 with Wine but I suspect it won't work.

Can anyone offer any advice? There must be someone with a working method to controlling the Guest OS's from Ubuntu

---

