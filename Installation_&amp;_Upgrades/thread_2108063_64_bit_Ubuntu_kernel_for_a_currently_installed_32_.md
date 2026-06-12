---
title: "64 bit Ubuntu kernel for a currently installed 32 bit userspace?"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by nerdopolis on 2013-01-23
Hi.

I was wondering if there was a simple way, either using dpkg Multiarch, or a .deb that reports itself as an i386 package to the package manager that contains a 64 bit Kernel and modules.

The reason why I ask is that although I have a 64 bit processor, when I installed my system in 2010, all I had was a 32 bit disk, and I currently don't really have much time to do a full reinstall,

And the reason I need a 64 bit kernel is so I can run 64 bit chroots so I can build 64 bit live cds.

(As a temporary solution, what I  had to do was boot a 64 bit live CD, passing init=/bin/bash as a kernel option, then mounting my drive, then bind mount over the /media/lib/modules/version, then using pivot_root, and then running exec /sbin/init. allowing me to use everything, except for VirtualBox because it's Kernel modules are not installed on the Live CD.) 

My only concern is if DKMS. would work...

---

### Post by tgalati4 on 2013-01-23
You could try a force install (dpkg -i --force-all), but that would probably break your system in subtle and not so subtle ways.  I would partition your hard drive or add a hard drive and do a proper 64-bit installation, and make it dual boot.  That way you still have your working distro and a new, 64-bit distro for making your disks and to migrate to in the future.

Unlike wikipedia, what you say sounds good in theory, but not in practice.

---

### Post by nerdopolis on 2013-01-23
> **tgalati4 said:**
> You could try a force install (dpkg -i --force-all), but that would probably break your system in subtle and not so subtle ways.  I would partition your hard drive or add a hard drive and do a proper 64-bit installation, and make it dual boot.  That way you still have your working distro and a new, 64-bit distro for making your disks and to migrate to in the future.

Unlike wikipedia, what you say sounds good in theory, but not in practice.

Oh.

I tried forcing multiarch for linux-generic, but ran into weirdness with the kernel headers, and dkms.

What I guess I'll have to do is install an *older* kernel with multiarch as 64 bit, and keep the linux-generic as 32 bit.

I'll switch between kernels from when I need to build my ISOs, and then use my 32 bit to use VirtualBox as it relies on dkms, and I'll still be able to retain using the same userspace and configurations.

---

