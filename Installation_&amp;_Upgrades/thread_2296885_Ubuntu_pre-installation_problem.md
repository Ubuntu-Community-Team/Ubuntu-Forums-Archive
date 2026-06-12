---
title: "Ubuntu pre-installation problem"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by Nicu34 on 2015-09-29
Hi everyone, i got a problem while I'm trying to install Ubuntu 14.04 from stick, dual boot with an Windows 8.1 64 bits on ACER ASPIRE ES1-512. If i try to install it on LEGACY mode, Ubuntu is booting, but it won't recognize other operating system (in this case Windows 8.1) and the others partitions. If i try in UEFI mode, the laptop shows me "No bootable device found". What should i do?

---

### Post by sudodus on 2015-09-29
Welcome to the Ubuntu Forums :-)

You should use a 64-bit (amd64) Ubuntu version for installation in UEFI mode, and you should use a tool that can create a pendrive that works in UEFI mode. Which tool did you use?

Furthermore it helps to turn off secure boot (in UEFI) and fast startup (in Windows).

Maybe you will find what you need in the following link (start with the two first links from it)

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by oldfred on 2015-09-29
UEFI & BIOS/CSM boot are not compatible. You can only dual boot from grub if all systems are installed in the same boot mode.

But Acer requires you to enable trust on the grub/ubuntu efi boot files.

 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

---

