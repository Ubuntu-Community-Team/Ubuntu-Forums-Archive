---
title: "Problem configuring open-vm-tools on 9.10"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by btomasini on 2009-11-18
I installed open-vm-tools, and when trying to configure, am getting an error building the kernel modules.  Below is the error:

[...]

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.31-14-generic/build/include] 

Extracting the sources of the vmmemctl module.

Building the vmmemctl module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config5/vmmemctl-only'
make -C /lib/modules/2.6.31-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /tmp/vmware-config5/vmmemctl-only/os.o
/tmp/vmware-config5/vmmemctl-only/os.c:36:27: error: driver-config.h: No such file or directory
/tmp/vmware-config5/vmmemctl-only/os.c:52:26: error: compat_sched.h: No such file or directory
/tmp/vmware-config5/vmmemctl-only/os.c:58:16: error: os.h: No such file or directory
/tmp/vmware-config5/vmmemctl-only/os.c:59:23: error: vmballoon.h: No such file or directory
/tmp/vmware-config5/vmmemctl-only/os.c:101: error: expected specifier-qualifier-list before ‘OSTimerHandler’
/tmp/vmware-config5/vmmemctl-only/os.c:112: error: expected specifier-qualifier-list before ‘OSStatusHandler’
/tmp/vmware-config5/vmmemctl-only/os.c:290: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OS_Identity’
/tmp/vmware-config5/vmmemctl-only/os.c:356: error: expected ‘)’ before ‘handle’
/tmp/vmware-config5/vmmemctl-only/os.c:383: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OS_ReservedPageAlloc’
/tmp/vmware-config5/vmmemctl-only/os.c:413: error: expected ‘)’ before ‘handle’
/tmp/vmware-config5/vmmemctl-only/os.c:439: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OS_TimerStart’
/tmp/vmware-config5/vmmemctl-only/os.c: In function ‘os_timer_thread_loop’:
/tmp/vmware-config5/vmmemctl-only/os.c:473: error: implicit declaration of function ‘compat_set_freezable’
/tmp/vmware-config5/vmmemctl-only/os.c:478: error: ‘os_timer’ has no member named ‘period’
/tmp/vmware-config5/vmmemctl-only/os.c:478: error: implicit declaration of function ‘compat_wait_check_freezing’
/tmp/vmware-config5/vmmemctl-only/os.c:478: error: ‘os_timer’ has no member named ‘delay’
/tmp/vmware-config5/vmmemctl-only/os.c:478: error: ‘os_timer’ has no member named ‘delay’
/tmp/vmware-config5/vmmemctl-only/os.c:482: error: implicit declaration of function ‘compat_try_to_freeze’
/tmp/vmware-config5/vmmemctl-only/os.c:488: error: ‘os_timer’ has no member named ‘handler’
/tmp/vmware-config5/vmmemctl-only/os.c:488: error: ‘os_timer’ has no member named ‘data’
/tmp/vmware-config5/vmmemctl-only/os.c: In function ‘OS_TimerStop’:
/tmp/vmware-config5/vmmemctl-only/os.c:514: error: ‘os_timer’ has no member named ‘task’
/tmp/vmware-config5/vmmemctl-only/os.c: In function ‘os_proc_show’:
/tmp/vmware-config5/vmmemctl-only/os.c:550: error: ‘os_status’ has no member named ‘handler’
/tmp/vmware-config5/vmmemctl-only/os.c:561: error: ‘os_status’ has no member named ‘handler’
/tmp/vmware-config5/vmmemctl-only/os.c: At top level:
/tmp/vmware-config5/vmmemctl-only/os.c:604: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘OS_Init’
/tmp/vmware-config5/vmmemctl-only/os.c: In function ‘OS_Cleanup’:
/tmp/vmware-config5/vmmemctl-only/os.c:670: error: ‘os_status’ has no member named ‘name_verbose’
/tmp/vmware-config5/vmmemctl-only/os.c: In function ‘init_module’:
/tmp/vmware-config5/vmmemctl-only/os.c:677: error: implicit declaration of function ‘Balloon_ModuleInit’
/tmp/vmware-config5/vmmemctl-only/os.c:677: error: ‘BALLOON_SUCCESS’ undeclared (first use in this function)
/tmp/vmware-config5/vmmemctl-only/os.c:677: error: (Each undeclared identifier is reported only once
/tmp/vmware-config5/vmmemctl-only/os.c:677: error: for each function it appears in.)
/tmp/vmware-config5/vmmemctl-only/os.c: In function ‘cleanup_module’:
/tmp/vmware-config5/vmmemctl-only/os.c:692: error: implicit declaration of function ‘Balloon_ModuleCleanup’
make[2]: *** [/tmp/vmware-config5/vmmemctl-only/os.o] Error 1
make[1]: *** [_module_/tmp/vmware-config5/vmmemctl-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [vmmemctl.ko] Error 2
make: Leaving directory `/tmp/vmware-config5/vmmemctl-only'
Unable to build the vmmemctl module.

The memory manager driver (vmmemctl module) is used by VMware host software to 
efficiently reclaim memory from a virtual machine.
If the driver is not available, VMware host software may instead need to swap 
guest memory to disk, which may reduce performance.
The rest of the software provided by VMware Tools is designed to work 
independently of this feature.
If you want the memory management feature, you can install the driver by 
running vmware-config-tools.pl again after making sure that gcc, binutils, make
and the kernel sources for your running kernel are installed on your machine. 
These packages are available on your distribution's installation CD.



Any help would be appreciated.

---

### Post by jfdill_2 on 2009-11-24
I have had the same error and no luck installing VMware tools using various methods, for example:

[https://answers.launchpad.net/ubuntu/+question/39005](https://answers.launchpad.net/ubuntu/+question/39005)

open-vm-tools may work as described in this article:

[http://langui.sh/2009/10/05/ubuntu-9-10-in-vmware/](http://langui.sh/2009/10/05/ubuntu-9-10-in-vmware/)

---

