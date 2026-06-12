---
title: "modules kvm and kvm_amd don't get loaded automatically anymore"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Captain_Kirk on 2010-04-09
since the last qemu-kvm upgrade it seems to be broken. No kvm modules are being loaded and "start qemu-kvm" exits with "start: Job failed to start". Maybe all these issues have been there before and I didn't notice them. Now, as a virt. machine doesn't boot with grub stage2 error I began searching for the problem. When I manually type "modprobe kvm" and "modprobe kvm_amd" the virt. machine will start as it did before the qemu-kvm upgrade.
(btw. I'm using the Virtual Machine Manager)

Anybody any ideas? Thanks!

---

### Post by Der_King on 2010-04-10
> **Captain_Kirk said:**
> since the last qemu-kvm upgrade it seems to be broken. No kvm modules are being loaded and "start qemu-kvm" exits with "start: Job failed to start". Maybe all these issues have been there before and I didn't notice them. Now, as a virt. machine doesn't boot with grub stage2 error I began searching for the problem. When I manually type "modprobe kvm" and "modprobe kvm_amd" the virt. machine will start as it did before the qemu-kvm upgrade.
(btw. I'm using the Virtual Machine Manager)

Anybody any ideas? Thanks!


Try to uncomment the line 
   "#SLEEP_MILLISECS=2000" 
in file
  /etc/default/qemu-kvm
and do a 
  start qemu-kvm

The kernel modules now get loaded, and kvm can be chosen as hypervisor. (And yes, a client did run using kvm).

---

### Post by Captain_Kirk on 2010-04-10
Hallo Der_King,

thanks, your hint is the solution for the problem!

---

