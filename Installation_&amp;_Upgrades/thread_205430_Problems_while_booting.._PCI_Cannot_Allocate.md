---
title: "Problems while booting.. PCI: Cannot Allocate"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by reneoctavio on 2006-06-28
I downloaded ubuntu6.06 desktop i386, I verified the md5sum and it's ok,I burned the cd. When I boot the cd, stay a long time in the screen with a logo of Ubuntu, I pressed alt+F1 and appears this:

PCI: Cannot allocate resource region 4 of device 0000:00:06.0
PCI: Cannot allocate resource region 0 of device 0000:01:00.0
PCI: Error while updating region 000:06:014(00001001=0000f001)
PCI: Failed to allocate mem resource #0:400000000@c0000000 for 0000:01:01.0

I tried the Brazilian Distro Kurumin 6 and also say the same thing.
The version 5.04 Hoary i386 or amd-64 works.
I also tried installing hoary and do an apt-get dist-upgrade, it's ok but the mouse, sound and network stop, and only work with the kernel of the hoary, the kernel version of dapper say the same thing I writed above

My computer is K8N4-E Deluxe, Semprom 2600+@2000, 1GB Memory Ram, PCIe Nvidia Geforce 6600 256MB. HD Seagate 80GB.
what I can do now? thanks for your helping.

---

### Post by mossmax62 on 2006-07-24
Hy from Chile, i have a very similar harware configuration, how do i for solve the problem....

Just put acpi=off at the begining of the boot options and when you finaly have the system installed, u go to /etc/grub/menu.lst,
edit and put a the end of kernel line acpi=off, that works for me and i know is a lot of people in the net seraching for this awnser, bye men.

Maxi Mussuto.

---

