---
title: "Server reboot - vmware servers won't start now!"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by aj997 on 2009-11-16
Hi guys

First post so please go easy if this is a common issue (I have done LOTS of googling and no solutions I have seen have worked yet).

Basically I am running: Ubuntu 9.04 (VMWare Server 2.0.1 Build 156745)

I have been running this fine for several months.

Anyway, the power on the box was cycled last weekend and now (after an OS update) the VM servers won't start back up in the console saying "Failed to initialize monitor device" for VirtualMachine.powerOn

Thus far I have tried:

1) Re-running vmware-config.pl (several times)
2) Uninstalling VMware
3) Re-installing as per: [https://help.ubuntu.com/community/VMware/Server#Ubuntu](https://help.ubuntu.com/community/VMware/Server#Ubuntu) 9.04 (VMWare Server 2.0.1 Build 156745)

All the installations throw zero errors, and I am using all default values for the installation script.

I have the same OS and VMware versions running just fine on another box (including latest 'apt-get update' and that works fine, so everything should be aligned.

I am at a loss what to try next.

Please help!!

Many thanks,

-Alex

---

### Post by aj997 on 2009-11-16
More info:

oracle@bigwig:~$ cd vmware-server-distrib
oracle@bigwig:~/vmware-server-distrib$ sudo patch ./bin/vmware-config.pl ~/vmware-config.pl.patch.txt
patching file ./bin/vmware-config.pl
oracle@bigwig:~/vmware-server-distrib$ sudo ./vmware-install.pl
Creating a new VMware Server installer database using the tar4 format.

Installing VMware Server.

In which directory do you want to install the binary files?
[/usr/bin]

The file /usr/bin/vmware-config.pl that this program was about to install
already exists. Overwrite? [yes]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/usr/sbin]

In which directory do you want to install the library files?
[/usr/lib/vmware]

The path "/usr/lib/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the manual files?
[/usr/share/man]

In which directory do you want to install the documentation files?
[/usr/share/doc/vmware]

The path "/usr/share/doc/vmware" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

The installation of VMware Server 2.0.1 build-156745 for Linux completed
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

[[truncated license]]

Do you accept? (yes/no) yes

Thank you.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.28-16-server/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmmon-only'
make -C /lib/modules/2.6.28-16-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-server'
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config2/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config2/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config2/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config2/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config2/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-server'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config2/vmmon-only'
The vmmon module loads perfectly into the running kernel.

None of the pre-built vmci modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmci module for
your system (you need to have a C compiler installed on your system)? [yes]

Extracting the sources of the vmci module.

Building the vmci module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmci-only'
make -C /lib/modules/2.6.28-16-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-server'
  CC [M]  /tmp/vmware-config2/vmci-only/linux/driver.o
  CC [M]  /tmp/vmware-config2/vmci-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config2/vmci-only/linux/vmciKernelIf.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciEvent.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciQueuePair.o
  CC [M]  /tmp/vmware-config2/vmci-only/common/vmciResource.o
  LD [M]  /tmp/vmware-config2/vmci-only/vmci.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config2/vmci-only/vmci.mod.o
  LD [M]  /tmp/vmware-config2/vmci-only/vmci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-server'
cp -f vmci.ko ./../vmci.o
make: Leaving directory `/tmp/vmware-config2/vmci-only'
The vmci module loads perfectly into the running kernel.

VMWare config patch VMCI!
`/tmp/vmware-config2/vmci-only/Module.symvers' -> `/tmp/vmware-config2/../Module.symvers'
None of the pre-built vsock modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vsock module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Extracting the sources of the vsock module.

VMWare config patch VSOCK!
`/tmp/vmware-config2/../Module.symvers' -> `/tmp/vmware-config2/vsock-only/Module.symvers'
Building the vsock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vsock-only'
make -C /lib/modules/2.6.28-16-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-server'
  CC [M]  /tmp/vmware-config2/vsock-only/linux/af_vsock.o
  CC [M]  /tmp/vmware-config2/vsock-only/linux/driverLog.o
  CC [M]  /tmp/vmware-config2/vsock-only/linux/util.o
/tmp/vmware-config2/vsock-only/linux/util.c: In function âVSockVmciLogPktâ:
/tmp/vmware-config2/vsock-only/linux/util.c:157: warning: format not a string literal and no format arguments
  CC [M]  /tmp/vmware-config2/vsock-only/linux/vsockAddr.o
  LD [M]  /tmp/vmware-config2/vsock-only/vsock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config2/vsock-only/vsock.mod.o
  LD [M]  /tmp/vmware-config2/vsock-only/vsock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-server'
cp -f vsock.ko ./../vsock.o
make: Leaving directory `/tmp/vmware-config2/vsock-only'
The vsock module loads perfectly into the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes]

Configuring a bridged network for vmnet0.

Please specify a name for this network.
[Bridged]

Your computer has multiple ethernet network interfaces available: eth0, virbr0.
Which one do you want to bridge to vmnet0? [eth0]

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no]

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]

Configuring a NAT network for vmnet8.

Please specify a name for this network. [NAT]

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

The subnet 192.168.90.0/255.255.255.0 appears to be unused.

The following NAT networks have been defined:

. vmnet8 is a NAT network on private subnet 192.168.90.0.

Do you wish to configure another NAT network? (yes/no) [no]

Do you want to be able to use host-only networking in your virtual machines?
[yes]

Configuring a host-only network for vmnet1.

Please specify a name for this network.
[HostOnly]

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

The subnet 172.16.200.0/255.255.255.0 appears to be unused.

The following host-only networks have been defined:

. vmnet1 is a host-only network on private subnet 172.16.200.0.

Do you wish to configure another host-only network? (yes/no) [no]

None of the pre-built vmnet modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmnet module for
your system (you need to have a C compiler installed on your system)? [yes]

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmnet-only'
make -C /lib/modules/2.6.28-16-server/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-16-server'
  CC [M]  /tmp/vmware-config2/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config2/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config2/vmnet-only/userif.o
  CC [M]  /tmp/vmware-config2/vmnet-only/netif.o
  CC [M]  /tmp/vmware-config2/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-config2/vmnet-only/filter.o
  CC [M]  /tmp/vmware-config2/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-config2/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-config2/vmnet-only/smac.o
  CC [M]  /tmp/vmware-config2/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-config2/vmnet-only/vnetUserListener.o
  LD [M]  /tmp/vmware-config2/vmnet-only/vmnet.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config2/vmnet-only/vmnet.mod.o
  LD [M]  /tmp/vmware-config2/vmnet-only/vmnet.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-16-server'
cp -f vmnet.ko ./../vmnet.o
make: Leaving directory `/tmp/vmware-config2/vmnet-only'
The vmnet module loads perfectly into the running kernel.

Please specify a port for remote connections to use [902]

Please specify a port for standard http connections to use [8222]

Please specify a port for secure http (https) connections to use [8333]

The current administrative user for VMware Server  is 'oracle'.  Would you like
to specify a different administrator? [no]

Using oracle as the VMware Server administrator.

You have a pre-existing authorization.xml.  The new version will be created as
/etc/vmware/hostd/NEW_authorization.xml.  Please check the new file for any new
values that you may need to migrate to your current authorization.xml.

You have a pre-existing vmInventory.xml.  The new version will be created as
/etc/vmware/hostd/NEW_vmInventory.xml.  Please check the new file for any new
values that you may need to migrate to your current vmInventory.xml.

In which directory do you want to keep your virtual machine files?
[/var/lib/vmware/Virtual Machines]

You have a pre-existing datastores.xml.  The new version will be created as
/etc/vmware/hostd/NEW_datastores.xml.  Please check the new file for any new
values that you may need to migrate to your current datastores.xml.

Do you want to enter a serial number now? (yes/no/help) [no]

Creating a new VMware VIX API installer database using the tar4 format.

Installing VMware VIX API.

In which directory do you want to install the VMware VIX API binary files?
[/usr/bin]

In which directory do you want to install the VMware VIX API library files?
[/usr/lib/vmware-vix/lib]

The path "/usr/lib/vmware-vix/lib" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

In which directory do you want to install the VMware VIX API document pages?
[/usr/share/doc/vmware-vix]

The path "/usr/share/doc/vmware-vix" does not exist currently. This program is
going to create it, including needed parent directories. Is this what you want?
[yes]

The installation of VMware VIX API 1.6.2 build-156745 for Linux completed
successfully. You can decide to remove this software from your system at any
time by invoking the following command: "/usr/bin/vmware-uninstall-vix.pl".

Enjoy,

--the VMware team

Starting VMware services:
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family:                           done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                   done
   Host-only networking on /dev/vmnet1 (background)                    done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet8 (background)                    done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   VMware Server Authentication Daemon (background)                    done
   Shared Memory Available                                             done
Starting VMware management services:
   VMware Server Host Agent (background)                               done
   VMware Virtual Infrastructure Web Access
Starting VMware autostart virtual machines:
   Virtual machines                                                    done

The configuration of VMware Server 2.0.1 build-156745 for Linux for this
running kernel completed successfully.

oracle@bigwig:~/vmware-server-distrib$ /etc/init.d/vmware-core status
Bridged networking on /dev/vmnet0 is running
Host network detection is not running
Host-only networking on /dev/vmnet1 is running
DHCP server on /dev/vmnet1 is not running
Host-only networking on /dev/vmnet8 is running
DHCP server on /dev/vmnet8 is not running
NAT networking on /dev/vmnet8 is running
Module vmmon loaded
Module vmnet loaded

---

