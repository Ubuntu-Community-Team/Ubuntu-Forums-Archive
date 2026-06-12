---
title: "Mouting volume to early in boot process"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by Erik-NA on 2011-06-10
I have a rocketraid 2710 card with a RAID-5 volume mounted in /etc/fstab in Ubuntu 11.04

During booting the Rocketraid driver have not finished the initializing process before the volume is mounted and the boot process is halted waiting for manual input.

The Rocketraid driver is installed in the kernel as a module. Is there any way to "activate" the module earlier in the boot process before the automatic mount starts?

---

### Post by Bobhuber on 2011-06-10
> **Erik-NA said:**
> I have a rocketraid 2710 card with a RAID-5 volume mounted in /etc/fstab in Ubuntu 11.04

During booting the Rocketraid driver have not finished the initializing process before the volume is mounted and the boot process is halted waiting for manual input.

The Rocketraid driver is installed in the kernel as a module. Is there any way to "activate" the module earlier in the boot process before the automatic mount starts?
This may help you. [https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)
I think the trick will be to mount the volume out of fsdisk after the initial boot process.

---

### Post by Erik-NA on 2011-06-11
I have the following entry in fstab

```
dev/sdc	/mnt/rocketraid	ext4	defaults	0	2

```

The Rocketraid driver is loaded too early in the boot process.

One solution is to create an own boot script which mounts the volume late in the boot process. 

However, isn't it possible to configure when the driver is loaded in the boot process?

---

