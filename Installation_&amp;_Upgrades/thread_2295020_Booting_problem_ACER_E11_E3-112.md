---
title: "Booting problem ACER E11 E3-112"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by deno3 on 2015-09-15
Hello,
I have a problem with booting Ubuntu after installing. It always turns on the GRUB with "try ubuntu... , install..." . And when I disconnect the USB it just shows me a small picture of HDD and says "no bootable device". I tried everything in BIOS, I disabled secure boot, I tried to use the boot repair program and it's still doing the same. This is the link from there :
[http://paste.ubuntu.com/12417758](http://paste.ubuntu.com/12417758)

btw. I'm new to ubuntu.

Thanks for your help.

*I want to use only Ubuntu on that laptop, so no dual boot

---

### Post by oldfred on 2015-09-15
I do not know why it says unknown device instead of the normal ubuntu.
And normally the efi partition is first or at least near beginning of drive. But I have seen one or two with it further into drive and they worked. Not sure what limit is. UEFI suggests first.

But Acer require you to set a supervisory password and set trust on the Ubuntu grub & shim boot files.

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
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)

---

