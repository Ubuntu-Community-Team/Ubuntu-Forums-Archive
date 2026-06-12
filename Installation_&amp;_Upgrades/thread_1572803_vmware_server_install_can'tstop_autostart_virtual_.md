---
title: "vmware server install can'tstop autostart virtual machine"
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by Jacksoniii on 2010-09-11
so I'm a windows master and linux, well i know what i've heard .. so yeah and what was required to pass the A+ test which wasn't much linux info. now I just installed it and have been struggling with many tutorials to instal VMWare, I already installed wine and can't run my video chat messenger windows clients like yahoo and camfrog properly, lots of crashing and direct 3d issues and can't open cams etc.. so i'm trying to put vmware server 2 on my system and run my windows partition in linux at the same time.. so i can still have my windows stuff while i learn on linux. But i can't get it installed correctly... now I'm not sure what all i've really done.. installed all types of vmware and rpacket software through synaptic package manager. uniinstalled some.. trying to us VM1.x from some tutorials for it to never quit work.. i had a server icon at one time but when i clicked it nothing would happen. my last attempt was on VMware 2 btw i'm ubuntu 10.04. and this is were i first notice the issue.

Stopping VMware autostart virtual machines:
   Virtual machines                                                   failed
Stopping VMware management services:
   VMware Virtual Infrastructure Web Access
   VMware Server Host Agent                                           failed
Stopping VMware services:
   VMware Authentication Daemon                                        done
   Virtual machine monitor                                             done

from there its just one thing after the next like...
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: script vmware-autostart: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'bridge-network-interface' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
insserv: script vmware-mgmt: service VMware already provided!
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'nmbd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.

eventually it ends with this:


Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.32-24-generic-pae/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.c:31:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:78: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config1/vmmon-only/./include/vmware.h:38,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:99:
/tmp/vmware-config1/vmmon-only/./include/vm_basic_types.h:108:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config1/vmmon-only/./common/vmx86.h:32,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.h:29,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:101:
/tmp/vmware-config1/vmmon-only/./include/x86msr.h:164:1: warning: "MSR_THERM2_CTL" redefined
In file included from /usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include/asm/msr.h:4,
                 from /usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include/asm/processor.h:21,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config1/vmmon-only/./include/compat_module.h:27,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:26:
/usr/src/linux-headers-2.6.32-24-generic-pae/arch/x86/include/asm/msr-index.h:228:1: warning: this is the location of the previous definition
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
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic-pae'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/go/unsup-linux-products" and 
"http://www.vmware.com/go/unsup-linux-tools".

Execution aborted.


I could really use some help here.

---

### Post by Jacksoniii on 2010-09-11
how do i delete this post.. i put it in a more appropriate place.. i think.

---

