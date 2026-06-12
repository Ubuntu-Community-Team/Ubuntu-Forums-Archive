---
title: "LVM Anyone?"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by Kyral on 2005-10-12
I'm installing Ubuntu Breezy (yah I know this is 5.04 Support) on machine in such a way that the entire rootfs and swap is on a LVM, with only the kernel, initrd.img, and System-Map being on a "physical" disk.

It installed fine, until I tried to reboot. Now keep in mind I couldn't install a bootloader because this is a lab machine and I had to use the current GRUB install. Anyway I try to reboot and the Kernel Panics because it can't sync the VFS, which I guess means it can't mount the LVMs. Anyone know how to fix this? Thanks!

---

