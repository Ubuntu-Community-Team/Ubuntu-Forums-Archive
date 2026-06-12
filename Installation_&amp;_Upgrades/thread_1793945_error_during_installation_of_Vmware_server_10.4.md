---
title: "error during installation of Vmware server 10.4"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by faisal.khan on 2011-06-30
Dear Sir,
                   i am facing some problem regarding vmware server installation error when i run this  "sudo ./vmware-install.pl" showing error for more details kindly see below message



The path "/usr/share/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]


The installation of VMware Server 2.0.2 build-203138 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this
program to invoke the command for you now? [yes]

Making sure services for VMware Server are stopped.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it.
NOTICE:  BY DOWNLOADING AND INSTALLING, COPYING OR OTHERWISE USING THE
SOFTWARE, YOU AGREE TO BE BOUND BY THE TERMS OF THIS VMWARE MASTER END
USER LICENSE AGREEMENT ("EULA").  IF YOU DO NOT AGREE TO THE TERMS OF
THIS EULA, YOU MAY NOT DOWNLOAD, INSTALL, COPY OR USE THE SOFTWARE, AND
YOU MAY RETURN THE UNUSED SOFTWARE TO THE VENDOR FROM WHICH YOU ACQUIRED
IT WITHIN THIRTY (30) DAYS AND REQUEST A REFUND OF THE LICENSE FEE, IF
ANY, ALREADY PAID UPON SHOWING PROOF OF PAYMENT.  "YOU" MEANS THE
NATURAL PERSON OR THE ENTITY THAT IS AGREEING TO BE BOUND BY THIS EULA,
THEIR EMPLOYEES AND THIRD PARTY CONTRACTORS THAT PROVIDE SERVICES TO
YOU.  YOU SHALL BE LIABLE FOR ANY FAILURE BY SUCH EMPLOYEES AND THIRD
PARTY CONTRACTORS TO COMPLY WITH THE TERMS OF THIS AGREEMENT.

1.      DEFINITIONS

1.1     "Designated Administrative Access" means that access to the
standard user interfaces of a given instance of the Software
(designated in this section) that you may grant to a designated
third party (a) for which you have provided advance written notice
to VMware that you are providing outsourced services and (b) for
whose dedicated benefit you have licensed such instance of the
Software.  Designated Administrative Access is applicable only
where you are 1) an IT outsourcing company that is providing
outsourced IT services to a client company and 2) applicable only

Do you accept? (yes/no) y

Thank you.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] y

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-28-server/build/include] /lib/modules/2.6.32-28-server/built/include

The path "/lib/modules/2.6.32-28-server/built/include" is not an existing
directory.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-28-server/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.32-28-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-server'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:31:
/tmp/vmware-config2/vmmon-only/./include/compat_wait.h:78: error: conflicting types for âpoll_initwaitâ
include/linux/poll.h:70: note: previous declaration of âpoll_initwaitâ was here
In file included from /tmp/vmware-config2/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:99:
/tmp/vmware-config2/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-28-server/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-28-server/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config2/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-28-server/arch/x86/include/asm/msr-index.h:230:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config2/vmmon-only/./include/vcpuset.h:103,
                 from /tmp/vmware-config2/vmmon-only/./include/modulecall.h:37,
                 from /tmp/vmware-config2/vmmon-only/./common/vmx86.h:33,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:101:
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:333:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:401:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:407:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:460:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:506:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:551:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:595:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:640:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:684:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:729:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:773:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:775:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:816:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:860:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:862:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:903:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:945:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:947:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:986:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1028:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1030:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1069:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1223:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1227:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1313:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1536:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_atomic.h:1796:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_asm_x86_64.h:39,
                 from /tmp/vmware-config2/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:103:
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:486:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:779:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:820:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86.h:922:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/./include/vm_asm.h:41,
                 from /tmp/vmware-config2/vmmon-only/linux/driver.c:103:
/tmp/vmware-config2/vmmon-only/./include/vm_asm_x86_64.h:56:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config2/vmmon-only/linux/driver.c:119:
/tmp/vmware-config2/vmmon-only/./common/hostif.h:53:7: warning: "WINNT_DDK" is not defined
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function âLinuxDriverSyncCallOnEachCPUâ:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1423: error: too many arguments to function âsmp_call_functionâ
/tmp/vmware-config2/vmmon-only/linux/driver.c: In function âLinuxDriver_Ioctlâ:
/tmp/vmware-config2/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âeuidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:1987: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âfsuidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:1988: error: âstruct task_structâ has no member named âuidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âegidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:1989: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âfsgidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:1990: error: âstruct task_structâ has no member named âgidâ
/tmp/vmware-config2/vmmon-only/linux/driver.c:2007: error: too many arguments to function âsmp_call_functionâ
make[2]: *** [/tmp/vmware-config2/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-server'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.

---

