---
title: "issue installing vmware server console in ubuntu 10.10"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by trojanworrier on 2011-05-25
hi, i'm new to ubuntu and new to installing anything. i'm facing error as follow while I try to install vmware:

sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
You have VMware Server archive: 
    VMware-server-2.0.2-203138.i386.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.35-28-generic package...
You do have the build-essential package...
You do have the patch package...
Found .tar file for vmci module
Found .tar file for vmmon-temp module
Found .tar file for vmnet-temp module
Found .tar file for vmmon module
Found .tar file for vsock module
Found .tar file for vmci-temp module
Found .tar file for vsock-temp module
Found .tar file for vmnet module
Extracting .tar files in order to apply the patch...
Untarring /home/arsh/Downloads/vmware-server-distrib/lib/modules/source/vmci.tar
Untarring /home/arsh/Downloads/vmware-server-distrib/lib/modules/source/vmmon-temp.tar
vmmon-temp.tar tarball failed to extract in the directory vmmon-temp-only. :(


please help how to install vmware console.

---

### Post by GOSSSAMER on 2011-07-20
I have the exact error using these instructions : [http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35](http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35)
 
Ive done it successfully in the past but for some reason it just doesnt work anymore.  
 
Im running "2.6.35-22-server #33-Ubuntu SMP Sun Sep 19 20:48:58 UTC 2010 x86_64 GNU/Linux"
 
Ive tried many suggestions I found online with no luck.  
 
 
Any help with this would appreciated.  
 
:confused:

---

### Post by xclusive585 on 2012-02-24
Ummmm BUMP!

Same issue with the [patch]("http://codebin.cotescu.com/vmware/vmware-server-2.0.x-kernel-2.6.3x-install.sh") on UBUNTU's (out-of-date?) vmware [howto]("https://help.ubuntu.com/community/VMware/Server")...

2.6.32-38 
10.04 lucid server

cannot find a working solution **anywhere**.

```
You have VMware Server archive:
        VMware-server-2.0.2-203138.x86_64.tar.gz
Checking for needed packages on Ubuntu
You do have the linux-headers-2.6.32-38-server package...
You do have the build-essential package...
You do have the patch package...
Found .tar file for vmnet module
Found .tar file for vmci-temp module
Found .tar file for vmnet-temp module
Found .tar file for vmci module
Found .tar file for vsock module
Found .tar file for vmmon-temp module
Found .tar file for vmmon module
Found .tar file for vsock-temp module
Extracting .tar files in order to apply the patch...
Untarring /home/administrator/here/vmware-server-distrib/lib/modules/source/vmnet.tar
Untarring /home/administrator/here/vmware-server-distrib/lib/modules/source/vmci-temp.tar
Untarring /home/administrator/here/vmware-server-distrib/lib/modules/source/vmnet-temp.tar
vmnet-temp.tar tarball failed to extract in the directory vmnet-temp-only. :(

```*If* that tarball would extract, I should be able to successfully run the vmware-config.pl and move on with my life!

It's not always the same tarball either, it can be any of the .tar's in that folder that pull this error while running the ubuntu patch

anyone know what I'm missing here.....?

2012... you'd think there would be a .deb by now, or better yet how bout apt-get install vmware!!!! What the hell, I choose ubuntu over pure debian simply because of the larger package base and support.
Vmware is popular, and Ubuntu is (or very soon will be) the most widely used distro out there. It's a shame vmware doesn't better support our specific distro.

---

### Post by xclusive585 on 2012-02-24
so I fixed the non-unpacking .tar's by removing the target (unpacked directory), and trying again. 
This time the script unpacked all of the .tar's into the vmware-server-distrib folder, as it should. 

however, upon running the vmware-install.pl located in the (patched) vmware-server-distrib directory, i get this error at the end of the process, and an incomplete install.
```
Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config3/vmmon-only'
make -C /lib/modules/2.6.32-38-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-38-server'
  CC [M]  /tmp/vmware-config3/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:31:
/tmp/vmware-config3/vmmon-only/./include/compat_wait.h:78: error: conflicting types for âpoll_initwaitâ
include/linux/poll.h:70: note: previous declaration of âpoll_initwaitâ was here
In file included from /tmp/vmware-config3/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:99:
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config3/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:101:
/tmp/vmware-config3/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-38-server/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-38-server/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config3/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-38-server/arch/x86/include/asm/msr-index.h:234:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config3/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:101:
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config3/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config3/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:103:
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config3/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config3/vmmon-only/linux/driver.c:103:
/tmp/vmware-config3/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config3/vmmon-only/linux/driver.c:119:
/tmp/vmware-config3/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function âLinuxDriverSyncCallOnEachCPUâ:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1423: error: too many arguments to function âsmp_call_functionâ
/tmp/vmware-config3/vmmon-only/linux/driver.c: In function âLinuxDriver_Ioctlâ:
/tmp/vmware-config3/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âeuidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âfsuidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âegidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âfsgidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config3/vmmon-only/linux/driver.c:2007: error: too many arguments to function âsmp_call_functionâ
make[2]: *** [/tmp/vmware-config3/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-38-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

```

still working through it. once I get to the bottom of all of this, I will try to make an updated howto for 10.04, seeing as how the [ubuntu community vmware document]("https://help.ubuntu.com/community/VMware/Server") offers only one paragraph, that leaves out any details that would be helpful to noobs, and just doesnt add up.

ubuntu community vmware says to just run the [script]("http://codebin.cotescu.com/vmware/vmware-server-2.0.x-kernel-2.6.3x-install.sh"), but all that script seems to do is download a patch or two, then patch and untar the vmware-server-distrib directory for you. still leaving you to run the vmware-install.pl even though it makes no mention of this in the tutorial.

---

