---
title: "Need help with installing VMWare Workstation 7.0 on Jaunty 9.04"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by darkhalo on 2010-01-03
Recently, I try to install the VMware Workstation to see if it works well. I download the vmware workstation 7.0 for vmware's website. and follow their instruction. Installation went smoothly except for some plugin is missing for eclipse, anyway, I think that is not that important for the plugin for eclipse is for debugging only. 
it told me the the installatio was sucessful, however, when I try to use the VMware player and VMware workstation, both of them have the VMware kernel module updater window pop up, and inside the windows

Before you can run VMware, several modules must be compiled and loaded into the running kernel.
Kernel Headers 2.6.32-custom-built-kernel
  Kernel headers for version 2.6.32-custom-built-kernel were not found. If you installed them in a non-default path you can specify the path below. Otherwise refer to your distribution's documentation for installation instructions and click Refresh to search again in default locations. 


The kernel version was compiled by me, and everything should be included. I also follow the procedure in [http://ubuntuforums.org/showthread.php?t=1139250&highlight=VMware+Workstation](http://ubuntuforums.org/showthread.php?t=1139250&highlight=VMware+Workstation) , utitl I use the comand 

```
sudo vmware-modconfig --console --install-all
```I got "gcc and kernel headers must be installed". Clearly, I installed gcc 3.4, 4.1,4.2,4.3, and the in my /usr/src folder, all the sources for gcc 4.1-4.3 and my linux-headers-2.6.32 are included. 

I don't know what to do next for I think everything it ask for is there, any advise?

---

### Post by darkhalo on 2010-01-03
It seems that when I use the generic kernel 2.6.17 ( the old one that I used) , the vmware workstation is working fine, but even when I tried back to use the generic kernel 2.6.32.2, it just can't reconfigure or recompile. Not to mention my custom compiled kernel. here is what I got

> $ sudo vmware-modconfig --console --install-all
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make -C /lib/modules/2.6.32-02063202-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-02063202-generic'
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/driverLog.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/linux/iommu.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/hashFunc.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-root/modules/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-root/modules/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-root/modules/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-02063202-generic'
make -C $PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= postbuild
make[1]: Entering directory `/tmp/vmware-root/modules/vmmon-only'
make[1]: `postbuild' is up to date.
make[1]: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-root/modules/vmmon-only'
Built vmmon module
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-root/modules/vmnet-only'
make -C /lib/modules/2.6.32-02063202-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. \
      MODULEBUILDDIR= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-02063202-generic'
  CC [M]  /tmp/vmware-root/modules/vmnet-only/driver.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/hub.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/userif.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/netif.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/bridge.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/filter.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/procfs.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac_compat.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/smac.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetEvent.o
  CC [M]  /tmp/vmware-root/modules/vmnet-only/vnetUserListener.o
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‘VNetUserListenerEventHandler’:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: (Each undeclared identifier is reported only once
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:240: error: for each function it appears in.)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c: In function ‘VNetUserListenerRead’:
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: ‘TASK_INTERRUPTIBLE’ undeclared (first use in this function)
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‘signal_pending’
/tmp/vmware-root/modules/vmnet-only/vnetUserListener.c:282: error: implicit declaration of function ‘schedule’
make[2]: *** [/tmp/vmware-root/modules/vmnet-only/vnetUserListener.o] Error 1
make[1]: *** [_module_/tmp/vmware-root/modules/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-02063202-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-root/modules/vmnet-only'
Unable to install vmnet


so, at the end, it seems it's the kernel version's problem. hope some experts could provide some help!

---

### Post by Chihiro Kuroki on 2010-01-06
Did you visit the following URL?:
[http://communities.vmware.com/message/1401588]("http://communities.vmware.com/message/1401588#1401588")
Good luck!;)

---

### Post by chinoxl3 on 2010-01-25
That worked great on my Ubuntu 9.10 x64. Thanks a bunch!

---

