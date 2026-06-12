---
title: "Office XP dual boot"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-15
Hi,
I have dual boot on Winxp. It seems everything was working perfect. But I updated system through AUTOMATIX and have installed DEBIAN as well. Problem is when I restart computer on the Boot window I am getting following lists:

"
Ubuntu Kernel 2.6.15-25-386
Ubuntu Kernal 2.6.15-25-386 (Recovery Mode)

Ubuntu Kernel 2.6.15-23-386
Ubuntu Kernal 2.6.15-23-386 (Recovery Mode)

Other Operating System

Microsoft Windows XP Operating System   "


My question is why I am seeing two different messages for Ubuntu version. Is this something I have configured Ubuntu twice OR this is because of DEBIAN I have installed through AUTOMATIX?

Thanks

---

### Post by bukwirm on 2006-06-15
Did you upgrade from a previous release of Ubuntu? If you did, a new version of the kernel probably was installed. To get rid of it, run 'sudo aptitude', select 'obsolete packages', and uninstall them (press (minus), then press 'g' twice.) NOTE: this will remove all packages aptitude thinks are obsolete.

---

### Post by vasimakhtar on 2006-06-15
Thanks. I have not upgrade any Ubuntu version, but I just run Automatix to install multimedia codecs and debian. Is it that I have two versions of Ubuntu installed in my PC? What do I do to get rid of one?

---

### Post by nanotube on 2006-06-15
just edit your file /boot/grub/menu.lst, and remove the entry for the older kernel version.

but, you might as well just leave it for "just in case". it doesn't hurt anything, you know. :)

---

### Post by vasimakhtar on 2006-06-15
Thanks. My question is, whether I am running two versions of Ubuntu? In that case may be UBUNTU is using more space by two different versions. But if this is just a message I think I should leave that as it is.

---

### Post by nanotube on 2006-06-16
[QUOTE=vasimakhtar]Thanks. My question is, whether I am running two versions of Ubuntu? In that case may be UBUNTU is using more space by two different versions. But if this is just a message I think I should leave that as it is.[/QUOTE]
not two versions of ubuntu, just two versions of the linux kernel. when you upgrade the kernel, the old one remains for just in case (if the new one has problems). a kernel takes up maybe 15megs of space. so it's not a big deal.

---

