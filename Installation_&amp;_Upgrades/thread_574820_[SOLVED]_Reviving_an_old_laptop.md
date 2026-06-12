---
title: "[SOLVED] Reviving an old laptop"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by Bliepo32 on 2007-10-13
Hello everyone,
I am reviving an old laptop with xubuntu 7.04, but I have one little problem. I do not have enough disk space (harddisk is just 2GB). I want to solve this by usibng an old USB-stick (2GB) as an harddisk. Is this possible?

---

### Post by kerry_s on 2007-10-13
please list your full specs.

other wise try->
go debian custom.
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

do the base install, that means when it comes to package selection uncheck them all.

after install log in as root
apt-get install xorg gdm xfce4 
reboot(ctrl+alt+delete)

---

### Post by tgalati4 on 2007-10-13
Damn Small Linux has a few options for using USB disks (both as a boot-up disk and as storage for your files).

---

### Post by Bliepo32 on 2007-10-14
Thanks for your suggestions, but the thing is, that I want to use my laptop for school stuff (including ICT lessons). So I want to have stuff like GIMP, Openoffice, and e.g. Perl. Isn't there a way to use the USB-stick as a sort of hard-drive?

---

### Post by kerry_s on 2007-10-14
> **Bliepo32 said:**
> Thanks for your suggestions, but the thing is, that I want to use my laptop for school stuff (including ICT lessons). So I want to have stuff like GIMP, Openoffice, and e.g. Perl. Isn't there a way to use the USB-stick as a sort of hard-drive?

try it, it should show up when you install if you have it plugged in. 
why don't you just buy a bigger drive?

what are your spec's? can it run those heavy app's?

---

### Post by Bliepo32 on 2007-10-17
Allright, I have finally finished the installation of Ubuntu. I have another problem now though. During the installation, installing GRUB failed. Then, I choose to install LILO, which also failed. So, at the moment, I have no bootloader. Any ideas on how to fix this?

---

