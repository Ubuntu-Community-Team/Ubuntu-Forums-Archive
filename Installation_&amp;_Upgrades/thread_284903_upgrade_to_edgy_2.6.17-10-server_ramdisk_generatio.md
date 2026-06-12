---
title: "upgrade to edgy 2.6.17-10-server: ramdisk generation"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by scrubadub on 2006-10-26
My problem is similar to bug 63402 when trying to upgrade from 6.06 LTS (server version) I have the following problem

Running depmod.
Finding valid ramdisk creators.
Failed to find suitable ramdisk generation tool for kernel version
2.6.17-10 on running kernel 2.6.15-26 in /usr/sbin/mkinitramfs
....
kinda blows up after failing to make the ramdisk, ues /usr/sbin/mkinitramfs exists and I haven't done anything crazy with it.

in the first reply to the bug i mentioned above this person seems to have the same problem
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63402]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63402")

> This also happens to me after a dist-upgrade. The kernel package can't create a ramdisk image, so system panics on boot, because it can't read the disk partition.

Running depmod.
Finding valid ramdisk creators.
Failed to find suitable ramdisk generation tool for kernel version
2.6.17-10-386 on running kernel 2.6.15-27-386 in /usr/sbin/mkinitramfs

any suggestions welcome

---

