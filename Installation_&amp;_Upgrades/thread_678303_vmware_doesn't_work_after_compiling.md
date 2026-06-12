---
title: "vmware doesn't work after compiling"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by taekr on 2008-01-25
Hi, all

I have been working on this problem for more than 3 days.. Can't figure it out.

I compiled the kernel 2.6.23.14... then vmware stops working. I looked for a solution and tried everything, I believe. I tried patch, vmware-any-any-update115.tar.gz as well.

I still have 'Virtual machine monitor and Virtual Ethernet' failed.

When I do '/usr/bin/vmware/', I get..

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

(I'm using VMware_Workstation_6.0.2)

Could you take a look at the following and tell what I can do to fix the problem?? I am so frustrated now!! T T ;;


sudo /usr/bin/vmware-config.pl
[sudo] password for mark:
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
Virtual machine monitor done
Blocking file system: done
Bridged networking on /dev/vmnet0 done
Host network detection done
DHCP server on /dev/vmnet1 done
Host-only networking on /dev/vmnet1 done
DHCP server on /dev/vmnet8 done
NAT service on /dev/vmnet8 done
Host-only networking on /dev/vmnet8 done
Virtual ethernet done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel. Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.23.14/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Unknown VMware Workstation 6.0.2 build 59824 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.23.14/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.23'
CC [M] /tmp/vmware-config0/vmmon-only/linux/driver.o
CC [M] /tmp/vmware-config0/vmmon-only/linux/driverLog.o
CC [M] /tmp/vmware-config0/vmmon-only/linux/hostif.o
CC [M] /tmp/vmware-config0/vmmon-only/common/comport.o
CC [M] /tmp/vmware-config0/vmmon-only/common/cpuid.o
CC [M] /tmp/vmware-config0/vmmon-only/common/hash.o
CC [M] /tmp/vmware-config0/vmmon-only/common/memtrack.o
CC [M] /tmp/vmware-config0/vmmon-only/common/phystrack.o
CC [M] /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Werror-implicit-function-declaration" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wno-pointer-sign" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV321]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV3]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageGSX1]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMCrossPage*, VMDriver*) [with VMCrossPage = VMCrossPageV2]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM_V4(VMDriver*, Vcpuid) [with VMCrossPage = VMCrossPageV4]’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘int Vmx86_RunVM(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2491: warning: ‘sysenterState.SysenterStateV45::rsp’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2492: warning: ‘sysenterState.SysenterStateV45::rip’ is used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:3028: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h: In function ‘void Task_Switch_V45(VMDriver*, Vcpuid)’:
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::validEIP’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::cs’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rsp’ may be used uninitialized in this function
/tmp/vmware-config0/vmmon-only/common/task_compat.h:2666: warning: ‘sysenterState.SysenterStateV45::rip’ may be used uninitialized in this function
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciContext.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciDatagram.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciDriver.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciDs.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciGroup.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciHashtable.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciProcess.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciResource.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmciSharedMem.o
CC [M] /tmp/vmware-config0/vmmon-only/common/vmx86.o
CC [M] /tmp/vmware-config0/vmmon-only/vmcore/compat.o
CC [M] /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
LD [M] /tmp/vmware-config0/vmmon-only/vmmon.o
Building modules, stage 2.
MODPOST 1 modules
CC /tmp/vmware-config0/vmmon-only/vmmon.mod.o
LD [M] /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-2.6.23'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Trying to find a suitable vmblock module for your running kernel.

None of the pre-built vmblock modules for VMware Workstation is suitable for
your running kernel. Do you want this program to try to build the vmblock
module for your system (you need to have a C compiler installed on your
system)? [yes]

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmblock-only'
make -C /lib/modules/2.6.23.14/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.23'

CC [M] /tmp/vmware-config0/vmblock-only/linux/block.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/control.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/dbllnklst.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/dentry.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/file.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/filesystem.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/inode.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/module.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/stubs.o
CC [M] /tmp/vmware-config0/vmblock-only/linux/super.o
LD [M] /tmp/vmware-config0/vmblock-only/vmblock.o
Building modules, stage 2.
MODPOST 1 modules
CC /tmp/vmware-config0/vmblock-only/vmblock.mod.o
LD [M] /tmp/vmware-config0/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-2.6.23'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config0/vmblock-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/parport0, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/parport1, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/parport2, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/parport3, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet0, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet1, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet8, and was about to remove
it. Somebody else apparently did it already.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [no]
Do you want networking for your virtual machines? (yes/no/help) [yes]

This program previously created the file /dev/vmnet2, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet3, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet4, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet5, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet6, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet7, and was about to remove
it. Somebody else apparently did it already.

This program previously created the file /dev/vmnet9, and was about to remove
it. Somebody else apparently did it already.

Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [wizard]

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

All your ethernet interfaces are already bridged.

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 172.16.224.0.

Do you wish to configure another NAT network? (yes/no) [no]

Do you want to be able to use host-only networking in your virtual machines?
[yes]

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet XXX.

Do you wish to configure another host-only network? (yes/no) [no]

Trying to find a suitable vmnet module for your running kernel.

None of the pre-built vmnet modules for VMware Workstation is suitable for your
running kernel. Do you want this program to try to build the vmnet module for
your system (you need to have a C compiler installed on your system)? [yes]

Extracting the sources of the vmnet module.

Building the vmnet module.

Unknown VMware Workstation 6.0.2 build 59824 detected. Building for Workstation 6.0.0.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmnet-only'
make -C /lib/modules/2.6.23.14/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-2.6.23'
CC [M] /tmp/vmware-config0/vmnet-only/driver.o
CC [M] /tmp/vmware-config0/vmnet-only/hub.o
CC [M] /tmp/vmware-config0/vmnet-only/userif.o
CC [M] /tmp/vmware-config0/vmnet-only/netif.o
CC [M] /tmp/vmware-config0/vmnet-only/bridge.o
CC [M] /tmp/vmware-config0/vmnet-only/filter.o
CC [M] /tmp/vmware-config0/vmnet-only/procfs.o
CC [M] /tmp/vmware-config0/vmnet-only/smac_compat.o
CC [M] /tmp/vmware-config0/vmnet-only/smac_linux.x386.o
LD [M] /tmp/vmware-config0/vmnet-only/vmnet.o
Building modules, stage 2.
MODPOST 1 modules
CC /tmp/vmware-config0/vmnet-only/vmnet.mod.o
LD [M] /tmp/vmware-config0/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-2.6.23'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config0/vmnet-only'
The module loads perfectly in the running kernel.

Do you want to install the Eclipse Integrated Virtual Debugger? You must have
the Eclipse IDE installed. [no]

Starting VMware services:
Virtual machine monitor failed
Blocking file system: done
Virtual ethernet failed
Bridged networking on /dev/vmnet0 done
Host network detection done
Host-only networking on /dev/vmnet1 (background) done
DHCP server on /dev/vmnet1 done
Host-only networking on /dev/vmnet8 (background) done
DHCP server on /dev/vmnet8 done
NAT service on /dev/vmnet8 done

The configuration of VMware Workstation 6.0.2 build-59824 for Linux for this
running kernel completed successfully.

You can now run VMware Workstation by invoking the following command:
"/usr/bin/vmware".

Enjoy,

--the VMware team
__________________

---

### Post by philhinz on 2008-01-26
I have seen a similar problem with vmware-player.  For some reason vmware installation succeeds but does not remove a flag that indicates it is configured correctly.  On my system, when I remove the file

/etc/vmware/not_configured

it then works fine.  Is this your problem?  

On a related note, I can't get vmware-player 2.02 to install correctly with the latest kernel for hardy (2.6.24).  It fails when trying to recompile the vmmon module. Anyone else seen this? (Yes, I know hardy is still in development, but I would like to debug this, if possible).

---

