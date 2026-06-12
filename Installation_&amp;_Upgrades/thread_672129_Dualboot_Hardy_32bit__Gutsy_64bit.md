---
title: "Dualboot Hardy 32bit / Gutsy 64bit"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by skillshot on 2008-01-19
Hi,

i just installed Gutsy64bit parallel to my Hardy32bit system, using different root-partitions but the same boot-partition. Now i can boot to my newly installed 64bit-system, but when booting to my old system it gets stuck with:

request_module: runaway loop modprobe binfmt-464c
request_module: runaway loop modprobe binfmt-464c
request_module: runaway loop modprobe binfmt-464c
request_module: runaway loop modprobe binfmt-464c
request_module: runaway loop modprobe binfmt-464c

I read some posts that this is caused by some 32bit/64bit issue, but none explained what exactly the problem is ...

Maybe someone here can shed some light on it for me?

Thx!

---

### Post by skulda on 2008-01-19
Afaik the kernel image is stored in the boot partition. Maybe your problem is, that your 32-bit System is trying to run with your 64-bit kernel and loading 32-bit modules fails.
Check for this in your boot partition and in /boot/grub/menu.lst
skulda

---

### Post by skillshot on 2008-01-21
I think the automatic rebuild of initrd's after i installed lvm2 is causing the trouble ... i'll try to boot via bootable cd to my old system ...

I'll have to take a look at the update-initramfs/initrd scripts ...

---

