---
title: "could not start recompiled kernel on Virtual Machine"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by marcocamejo on 2011-12-13
I have a Dell Laptop with Ubuntu 11.10 installed. It is the Host for 3 Virtual Machines (also running Ubuntu 11.10) installed using KVM.

I need to recompile the kernel of each Virtual Machines for setting some networks options, but when trying to boot on the new Kernel I get the "Gave up waiting for root device".... "ALERT! /dev/disk/by-uuid/(ID) does not exist".

What I have tried:
1) rootdelay 50, 60, ... didn't work
2) booting with pci=nomsi (and other options)... didn't work
3) Deleting the partition and starting from scratch... got the same error.

Additiona info:
1) The Kernel on my PC and VMs is 3.0.0.12-generic-pae
2) The Kernel I am trying to compile is 3.0.1
3) There is no /etc/fstab when trying to boot from the new kernel
4) the uuid that the new kernel is not finding is exactly the one I see on the /etc/fstab of the original kernel

Can anybody help me?

---

