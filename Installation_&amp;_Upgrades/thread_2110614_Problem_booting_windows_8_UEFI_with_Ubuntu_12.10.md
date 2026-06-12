---
title: "Problem booting windows 8 UEFI with Ubuntu 12.10"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by evolvedlight on 2013-01-30
Hi

I installed Ubuntu 12.10 alongside Windows 8 after disabling secureboot. I had to mess around with /etc/grub2/40_custom to get it to work but I did in the end..

I had to reinstall Ubuntu as an upgrade broke the graphics card drivers - but I've got stuck making it work again. I thought I did the same steps, but it's failing with an error.

Boot-repair info: [http://paste.ubuntu.com/1590916/](http://paste.ubuntu.com/1590916/)
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(1,800,2f000,4ed7ca12f76d1d48,a0,f)/File(\efi\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire

Thanks!
Steve

---

### Post by evolvedlight on 2013-01-30
Oh, never mind. Looks like the option "Replace Ubuntu 12.10" button on the installer just wipes Windows and the recovery partition. Great times.

---

