---
title: "VMWare Workstation 5.5: vmmon incorrect version?"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by siorai on 2005-12-01
So I dilligently went through the wiki: [https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29]("https://wiki.ubuntu.com/InstallingVMWare?highlight=%28vmware%29") and it installed fine except for when it was building the vmmon module I saw this:

```
Building the vmmon module.

VMware 2 or VMware Express detected, building for VMware 2, VMware Express and VMware Workstation 4.0.x.
Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.12-10-686-smp/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686-smp'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
cc1plus: warning: command line option "-ffreestanding" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wdeclaration-after-statement" is valid for C/ObjC but not for C++
cc1plus: warning: command line option "-Wstrict-prototypes" is valid for Ada/C/ObjC but not for C++
```

Edit: Forgot to add that when I try to power on my virtual machine, I get this error:

```
 Version mismatch with vmmon module: expecting 133.0, got 122.0. You have an incorrect version of 'vmmon' kernel module. Try reinstalling VMWare Workstation
```

I am definitely trying to install VMWare Workstation 5.5. Is this due to remnants of the VMWare player install I did? I did use the uninstall script for it. If that's the case, how would I go about totally cleaning my system off so I can install Workstation properly?

---

### Post by woland on 2005-12-26
Have the same problem. Didn't find the solution yet. :(

---

### Post by woland on 2005-12-26
Found it here.
[http://www.ubuntuforums.org/showthread.php?t=107063](http://www.ubuntuforums.org/showthread.php?t=107063)

---

