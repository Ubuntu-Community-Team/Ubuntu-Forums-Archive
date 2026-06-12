---
title: "Ubuntu 16.04 LTS with Windows 10 (dual boot) doesn't work"
date: 2017-04-29
forum: Installation &amp; Upgrades
---

### Post by waterresistro on 2017-04-29
Hi guys, i just bought a new Acer desktop(if it has any relevance) with Windows 10 preinstalled and i'm trying to install Ubuntu 16.04 LTS.
After i boot from a stick and complete the instalation, it demands for reboot and then it just goes into Windows 10 like nothing happened. 
If i check the partition created for the linux instalation it shows "Unallocated".
I'm not sure what i'm doing wrong...

---

### Post by oldfred on 2017-04-29
Every Acer we have seen needs an UEFI supervisory password (never lose that or reset when done) and enabling "trust" on the grub/ubuntu .efi boot files in the ESP - efi system partition from within the UEFI.

Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)

---

### Post by waterresistro on 2017-05-06
Thanks for your answer oldfred, but the problem seems to be slightly different because the installation part doesn't go well (as the partition is empty) and the Select UEFI file as trusted.. option doesn't exist here. it's just a different menu.

p.s. i used Rufus to make the boot usb and i tried with MBR partition for UEFI or BIOS, and also with GPT partition for UEFI.
i also tried installing with uefi Secure Boot enabled and disabled.

---

### Post by Geoffrey_Arndt on 2017-05-06
Did you also disable any Win10 fast/quick boot (which requires Windows hibernation - - and often prevents installer from seeing all the partitions).

Additionally, I would suggest to use gparted to format unallocated to ext4, AND to use the "Something Else" option to allow for better control of where to put Ubuntu and swap partitions.   Be sure to mount system using / . . not necessary to have separate boot or home partitions.

The supervisor password is needed _to access additional setup screens_ to allow for usb persistent boot &  for special on/demand boot (one time boot selection menu).   (usually F12 on Acers).

Re Linux bootable devices, I now recommend Etcher over other common tools to create the usb boot stick.   [https://etcher.io/](https://etcher.io/)

Note:   Ubuntu should likely be installed from UEFI mode versus Legacy MBR mode (as Win10 installed via UEFI mode by default).

---

### Post by waterresistro on 2017-05-06
I just noticed in gparted the partition it's actually NOT empty, i seems all the files are there. So i guess the installation is ok.

Fast Startup was disabled in win10 but for some reason, if i mount the windows partition, it says that it is in hybernation mode.

 I also used etcher to create the bootable usb.

the setup has a sup0ervisor password set and it boots in UEFI mode i guess(all boot options have UEFI as value)

---

### Post by Geoffrey_Arndt on 2017-05-07
Did you set up ("after" entering a supervisor password) . . the F12 one time-boot menu?    This should provide one way to boot into Ubuntu (not the only way, but it works.)

---

