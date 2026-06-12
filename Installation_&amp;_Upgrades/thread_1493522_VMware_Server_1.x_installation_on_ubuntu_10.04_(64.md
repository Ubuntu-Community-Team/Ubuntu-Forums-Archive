---
title: "VMware Server 1.x installation on ubuntu 10.04 (64 bit) -- Failing"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by nitish.shivananda on 2010-05-25
Hi, 

I would like to install vmware sever 1 on my new ubuntu 10.04. (64 bit)  but its failing again and again. Below is the complete output. Kindly help me..

root@nitish-workstation:/home/nitish/vmware# cd vmware-server-distrib
root@nitish-workstation:/home/nitish/vmware/vmware-server-distrib# sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Server.

 * Stopping internet superserver xinetd                                                                                                                                                       [ OK ] 
 * Starting internet superserver xinetd                                                                                                                                                       [ OK ] 
insserv: warning: script 'K20acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'qemu-kvm' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'bridge-network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'acpid' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'alsa-mixer-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'avahi-daemon' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-manager' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'libvirt-bin' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'gdm' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'anacron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: script 'acpi-support' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dbus' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv:  loop involving service pulseaudio at depth 3
insserv:  loop involving service rsyslog at depth 2
insserv:  loop involving service udev at depth 1
insserv: There is a loop between service rsyslog and pulseaudio if stopped
insserv:  loop involving service dbus at depth 2
insserv: exiting now without changing boot order!
Stopping VMware services:
   Virtual machine monitor                                             done

Unable to get the last modification timestamp of the file 
/usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0.

File /usr/bin/vmware-config.pl is backed up to /usr/bin/vmware-config.pl.old.3.


File /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 is backed up to 
/usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.old.0.

This program previously created the directory 
/usr/lib/vmware/lib/libgcc_s.so.1, and was about to remove it. Since there are 
files in that directory that this program did not create, it will not be 
removed.

This program previously created the directory /usr/lib/vmware/lib, and was 
about to remove it. Since there are files in that directory that this program 
did not create, it will not be removed.

This program previously created the directory /usr/lib/vmware, and was about to
remove it. Since there are files in that directory that this program did not 
create, it will not be removed.

The removal of VMware Server 1.0.5 build-80187 for Linux completed 
successfully. Thank you for having tried this software.

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
[/usr/lib/vmware] 

In which directory do you want to install the manual files? 
[/usr/share/man] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware] 

The path "/usr/share/doc/vmware" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

readdir() attempted on invalid dirhandle LS at ./vmware-install.pl line 458.
closedir() attempted on invalid dirhandle LS at ./vmware-install.pl line 459.
The installation of VMware Server 1.0.5 build-80187 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall.pl".

Before running VMware Server for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config.pl". Do you want this 
program to invoke the command for you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

You must read and accept the End User License Agreement to continue.
Press enter to display it. 

VMWARE MASTER END USER LICENSE AGREEMENT

NOTICE:  BY DOWNLOADING AND INSTALLING, 
COPYING OR OTHERWISE USING THE SOFTWARE, YOU 
AGREE TO BE BOUND BY THE TERMS OF THIS EULA.  
IF YOU DO NOT AGREE TO THE TERMS OF THIS EULA, 
YOU MAY NOT DOWNLOAD, INSTALL, COPY OR USE THE 
SOFTWARE, AND YOU MAY RETURN THE UNUSED 
SOFTWARE TO THE VENDOR FROM WHICH YOU ACQUIRED 
IT WITHIN THIRTY (30) DAYS AND REQUEST A 
REFUND OF THE LICENSE FEE, IF ANY, ALREADY 
PAID UPON SHOWING PROOF OF PAYMENT.


Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-22-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config14/vmmon-only'
make -C /lib/modules/2.6.32-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/vmware-config14/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config14/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:48:
/tmp/vmware-config14/vmmon-only/./include/vm_basic_types.h:104:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config14/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:48:
/tmp/vmware-config14/vmmon-only/./include/vm_basic_types.h:159: error: redefinition of typedef ‘uintptr_t’
include/linux/types.h:41: note: previous declaration of ‘uintptr_t’ was here
In file included from /tmp/vmware-config14/vmmon-only/./include/x86.h:20,
                 from /tmp/vmware-config14/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:49:
/tmp/vmware-config14/vmmon-only/./include/x86apic.h:79:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/apic.h:11,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/smp.h:13,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/mmzone_64.h:12,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/mmzone.h:4,
                 from include/linux/mmzone.h:783,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/apicdef.h:136:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config14/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config14/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:49:
/tmp/vmware-config14/vmmon-only/./include/x86desc.h:593:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config14/vmmon-only/./include/machine.h:24,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:49:
/tmp/vmware-config14/vmmon-only/./include/x86.h:830:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/irqflags.h:60,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:12:
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/pgtable_types.h:182:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config14/vmmon-only/./include/vcpuset.h:78,
                 from /tmp/vmware-config14/vmmon-only/./include/modulecall.h:22,
                 from /tmp/vmware-config14/vmmon-only/./common/vmx86.h:18,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.h:16,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:49:
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:226:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:230:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:298:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:304:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:357:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:402:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:446:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:489:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:533:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:576:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:620:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:663:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:665:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:705:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:748:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:750:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:790:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:831:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:833:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:871:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:912:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:914:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:952:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:1073:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:1077:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:1124:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:1329:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:1454:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_atomic.h:1587:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config14/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:49:
/tmp/vmware-config14/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config14/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config14/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:49:
/tmp/vmware-config14/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config14/vmmon-only/./include/vm_asm_x86_64.h:23,
                 from /tmp/vmware-config14/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:52:
/tmp/vmware-config14/vmmon-only/./include/vm_asm_x86.h:430:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_asm_x86.h:676:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config14/vmmon-only/./include/vm_asm_x86.h:716:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config14/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:52:
/tmp/vmware-config14/vmmon-only/./include/vm_asm_x86_64.h:40:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config14/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config14/vmmon-only/linux/driver.c:71:
/tmp/vmware-config14/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config14/vmmon-only/linux/driver.c:146: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config14/vmmon-only/linux/driver.c:147: warning: initialization from incompatible pointer type
/tmp/vmware-config14/vmmon-only/linux/driver.c:150: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config14/vmmon-only/linux/driver.c:151: warning: initialization from incompatible pointer type
/tmp/vmware-config14/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Ioctl’:
/tmp/vmware-config14/vmmon-only/linux/driver.c:1654: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1654: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1655: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1655: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1656: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1656: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1657: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1657: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1659: error: ‘struct mm_struct’ has no member named ‘dumpable’
/tmp/vmware-config14/vmmon-only/linux/driver.c:1670: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config14/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config14/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config14/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@nitish-workstation:/home/nitish/vmware# cd vmware-any-any-update116
root@nitish-workstation:/home/nitish/vmware/vmware-any-any-update116# sudo ./runme.pl
Updating /usr/bin/vmware-config.pl ... now patched
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 

Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

/usr/share/applications/vmware-server.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-server.desktop: error: (will be fatal in the future): value "Emulator" in key "Categories" in group "Desktop Entry" requires another category to be present among the following categories: System, or Game
/usr/share/applications/vmware-server.desktop: error: (will be fatal in the future): value "Emulator;" for key "Categories" in group "Desktop Entry" does not contain a registered main category
/usr/share/applications/vmware-console-uri-handler.desktop: warning: value "vmware-server.png" for key "Icon" in group "Desktop Entry" is an icon name with an extension, but there should be no extension as described in the Icon Theme Specification if the value is not an absolute path
/usr/share/applications/vmware-console-uri-handler.desktop: error: (will be fatal in the future): value "Emulator" in key "Categories" in group "Desktop Entry" requires another category to be present among the following categories: System, or Game
/usr/share/applications/vmware-console-uri-handler.desktop: error: (will be fatal in the future): value "Emulator;" for key "Categories" in group "Desktop Entry" does not contain a registered main category
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.32-22-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Building for VMware Server 1.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config15/vmmon-only'
make -C /lib/modules/2.6.32-22-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /tmp/vmware-config15/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config15/vmmon-only/./include/vmware.h:25,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:52:
/tmp/vmware-config15/vmmon-only/./include/vm_basic_types.h:97:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config15/vmmon-only/./include/x86.h:21,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:53:
/tmp/vmware-config15/vmmon-only/./include/x86apic.h:80:1: warning: "APIC_BASE_MSR" redefined
In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/apic.h:11,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/smp.h:13,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/mmzone_64.h:12,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/mmzone.h:4,
                 from include/linux/mmzone.h:783,
                 from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:16:
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/apicdef.h:136:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config15/vmmon-only/./include/x86.h:24,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.h:15,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:53:
/tmp/vmware-config15/vmmon-only/./include/x86paging.h:61:1: warning: "PTE_PFN_MASK" redefined
In file included from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/paravirt.h:7,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/irqflags.h:60,
                 from include/linux/irqflags.h:57,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/system.h:11,
                 from /usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/processor.h:17,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:16:
/usr/src/linux-headers-2.6.32-22-generic/arch/x86/include/asm/pgtable_types.h:182:1: warning: this is the location of the previous definition
In file included from /tmp/vmware-config15/vmmon-only/./include/vcpuset.h:89,
                 from /tmp/vmware-config15/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config15/vmmon-only/./common/vmx86.h:19,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.h:16,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:53:
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:273:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:277:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:345:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:351:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:404:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:450:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:495:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:539:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:584:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:628:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:673:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:717:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:719:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:760:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:804:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:806:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:847:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:889:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:891:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:930:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:972:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:974:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:1013:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:1167:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:1171:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:1257:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:1470:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:1597:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_atomic.h:1730:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config15/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config15/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:53:
/tmp/vmware-config15/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config15/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config15/vmmon-only/./include/vmci_kernel_defs.h:26,
                 from /tmp/vmware-config15/vmmon-only/./common/vmciContext.h:19,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.h:21,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:53:
/tmp/vmware-config15/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:70: note: previous declaration of ‘poll_initwait’ was here
In file included from /tmp/vmware-config15/vmmon-only/./include/vm_asm_x86_64.h:25,
                 from /tmp/vmware-config15/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:56:
/tmp/vmware-config15/vmmon-only/./include/vm_asm_x86.h:479:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_asm_x86.h:772:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config15/vmmon-only/./include/vm_asm_x86.h:812:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config15/vmmon-only/./include/vm_asm.h:28,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:56:
/tmp/vmware-config15/vmmon-only/./include/vm_asm_x86_64.h:42:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config15/vmmon-only/linux/driver.c:83:
/tmp/vmware-config15/vmmon-only/./common/hostif.h:39:7: warning: "WINNT_DDK" is not defined
In file included from /tmp/vmware-config15/vmmon-only/linux/vmhost.h:13,
                 from /tmp/vmware-config15/vmmon-only/linux/driver.c:84:
/tmp/vmware-config15/vmmon-only/./include/compat_semaphore.h:5:27: error: asm/semaphore.h: No such file or directory
/tmp/vmware-config15/vmmon-only/linux/driver.c:171: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config15/vmmon-only/linux/driver.c:172: warning: initialization from incompatible pointer type
/tmp/vmware-config15/vmmon-only/linux/driver.c:175: error: unknown field ‘nopage’ specified in initializer
/tmp/vmware-config15/vmmon-only/linux/driver.c:176: warning: initialization from incompatible pointer type
/tmp/vmware-config15/vmmon-only/linux/driver.c: In function ‘LinuxDriver_Open’:
/tmp/vmware-config15/vmmon-only/linux/driver.c:558: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config15/vmmon-only/linux/driver.c: In function ‘__LinuxDriver_Ioctl’:
/tmp/vmware-config15/vmmon-only/linux/driver.c:1495: error: ‘struct task_struct’ has no member named ‘suid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1496: error: ‘struct task_struct’ has no member named ‘cap_permitted’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1761: error: ‘struct task_struct’ has no member named ‘euid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1761: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1762: error: ‘struct task_struct’ has no member named ‘fsuid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1762: error: ‘struct task_struct’ has no member named ‘uid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1763: error: ‘struct task_struct’ has no member named ‘egid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1763: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1764: error: ‘struct task_struct’ has no member named ‘fsgid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1764: error: ‘struct task_struct’ has no member named ‘gid’
/tmp/vmware-config15/vmmon-only/linux/driver.c:1781: error: too many arguments to function ‘smp_call_function’
make[2]: *** [/tmp/vmware-config15/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config15/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config15/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.


==================================================

I can see the VMware Server Console  icon in Applications -> Other.

But when I click on that its not invoking the VMware GUI.

Kindly help me resolving this issue.

Regards,
Nitish

---

### Post by p0c4r1 on 2010-06-08
same problem bro...

any one can help?

---

### Post by duren on 2010-06-19
I applied the vmware-update-2.6.31-5.5.9 patch which got me a little further, now I get this:

  CC [M]  /tmp/vmware-config3/vmmon-only/common/vmciContext.o
In file included from /tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:24,
                 from /tmp/vmware-config3/vmmon-only/common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/vmciContext.c:20:
/tmp/vmware-config3/vmmon-only/./include/vm_basic_types.h:97:7: warning: "__FreeBSD__" is not defined
In file included from /tmp/vmware-config3/vmmon-only/common/vmciContext.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/vmciContext.c:20:
/tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h: In function ‘VMCIHost_SignalCall’:
/tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:322: error: ‘TASK_NORMAL’ undeclared (first use in this function)
/tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:322: error: (Each undeclared identifier is reported only once
/tmp/vmware-config3/vmmon-only/./include/vmci_kernel_defs.h:322: error: for each function it appears in.)
In file included from /tmp/vmware-config3/vmmon-only/./include/vcpuset.h:107,
                 from /tmp/vmware-config3/vmmon-only/./include/modulecall.h:23,
                 from /tmp/vmware-config3/vmmon-only/common/vmx86.h:19,
                 from /tmp/vmware-config3/vmmon-only/common/hostif.h:18,
                 from /tmp/vmware-config3/vmmon-only/common/vmciContext.c:30:
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:273:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:277:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:345:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:351:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:404:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:450:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:495:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:539:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:584:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:628:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:673:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:717:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:719:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:760:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:804:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:806:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:847:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:889:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:891:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:930:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:972:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:974:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1013:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1167:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1171:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1257:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1470:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1597:7: warning: "_MSC_VER" is not defined
/tmp/vmware-config3/vmmon-only/./include/vm_atomic.h:1730:7: warning: "_MSC_VER" is not defined
In file included from /tmp/vmware-config3/vmmon-only/common/vmciContext.c:30:
/tmp/vmware-config3/vmmon-only/common/hostif.h:39:7: warning: "WINNT_DDK" is not defined
make[2]: *** [/tmp/vmware-config3/vmmon-only/common/vmciContext.o] Error 1
make[1]: *** [_module_/tmp/vmware-config3/vmmon-only] Error 2
make[1]: Leaving directory `/media/data/temp/linux-source-2.6.32'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config3/vmmon-only'
Unable to build the vmmon module.

---

### Post by duren on 2010-06-19
Figured it out..

It was quite similar to the issue [here]("http://communities.vmware.com/message/1475988").

Except that I had to edit */usr/lib/vmware/modules/source/vmmon.tar/vmmon-only/include/vmci_kernel_defs.h* where the section 

```
#include "vm_basic_types.h"
#ifdef linux
#include "compat_wait.h"
#include "compat_interrupt.h"
#include "compat_spinlock.h"
#include "compat_slab.h"
#endif // linux
```

became...

```
#include "vm_basic_types.h"
#ifdef linux
#include "compat_wait.h"
#include "compat_interrupt.h"
#include "compat_spinlock.h"
#include "compat_slab.h"
**#include "compat_sched.h"**
#endif // linux
```

**_NOTE 1:_** Of course you would have (assuming you're in the */usr/lib/vmware/modules/source/* folder)

1. Opened up the tar with: ```
tar -xvf vmmon.tar
```
2. Backed up the existing module: ```
mv vmmon.tar vmmon.tar.bak
```
3. Made the edit mentioned above.

4. Packaged it back up with ```
tar -cvf vmmon.tar vmmon-only/
```

**_NOTE 2_**: The update mentioned in my previous post can be obtained [ here.]("http://www.insecure.ws/warehouse/vmware-update-2.6.31-5.5.9.tar.bz2"). 

Use like so:

```
wget -c http://www.insecure.ws/warehouse/vmware-update-2.6.31-5.5.9.tar.bz2
tar xvfj vmware-update*.tar.bz2
cd vmware-update-2.6.31-5.5.9
./runme.pl
```

That got the show on the road.. :guitar:

[I]make: Leaving directory `/tmp/vmware-config5/vmnet-only'
The module loads perfectly in the running kernel.

.
.
.

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done

The configuration of VMware Server 1.0.10 build-203137 for Linux for this 
running kernel completed successfully.[/I]

**_NOTE 3_**: This is all assuming you've compiled your own kernel as explained [here]("http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-a-kubuntu-10.04-desktop-p2") which puts init_mm back in.

Hope this helps someone.

---

### Post by duren on 2010-06-19
PS: If the mui login locks you out (permission denied) the problem is that ia32-libs in 10.04 are missing the pam modules (*/lib32/security/pam*.so*). (vmware is requesting the 32bit libs for auth).

To solve this problem, I used mc (midnight commander) to peer into my 32bit distro and grab the pam modules out of the *iso/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu2_i386.deb* package and popped them into /lib32/security where they belong..

then I modified */etc/pam.d/vmware-authd* to look like this
```
#%PAM-1.0
auth       sufficient       /lib32/security/pam_unix.so shadow nullok
auth       required         /lib32/security/pam_unix_auth.so shadow nullok
account    sufficient       /lib32/security/pam_unix.so
account    required         /lib32/security/pam_unix_acct.so
```

.. to have it use the correct modules. I looked at many other posts regarding the modification of this file and nothing helped.

Finally, I can start using this archaic software. I wish they didn't switch to web based nonsense in v2, then I wouldn't have to worry about this old version.

They are attached for your convenience.

---

