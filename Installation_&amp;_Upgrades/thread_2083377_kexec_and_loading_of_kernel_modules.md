---
title: "kexec and loading of kernel modules"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by jdehart1 on 2012-11-12
When I do a kexec to reboot to a new kernel do the old kernel modules
stay loaded?

Here is my scenario. In a network testbed that we operate, when a system
is rebooted, we first do a PXE boot so we can check the system to see
if it needs to be re-installed. If it does not then we mount the local disk
and kexec the kernel resident on it. I am currently working on upgrading
the ixgbe driver on one of those systems but when I reboot and do the
kexec I continue to have the older driver which is resident in the PXE boot image
instead of the new driver that is now on the local disk.

In case it matters, I'm running Ubuntu 12.04.

Thanks for any help.

---

### Post by dino99 on 2012-11-12
i've no clue about your config, but it seems you run kexec on the default path, instead of the one you want to load.
you can check with blkid to be sure.

---

### Post by jdehart1 on 2012-11-19
I think I figured this out. 
Turns out I wasn't considering the case where the ixgbe driver was
built into the vmlinuz file and was loaded at boot each time.

---

