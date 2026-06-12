---
title: "HELP!!!  boot bring up grub prompt !"
date: 2017-06-16
forum: Installation &amp; Upgrades
---

### Post by rajaramk8 on 2017-06-16
Hello,
   I have installed ubuntu 16.04 alongside windows ( 8 or 10 - cant remember). 


Windows came with OEM. I had installed ubuntu. 


After ubuntu and windows upgrades - by grub got messed up and only windows was working. 


I booted from a persistent ubuntu usb and tried fixing grub using chroot method.  That messed up further. Even windows stopped booting. 


I did a fresh install on top of existing ubuntu 16.04 on the hard disk from the same persistent usb stick.


A fresh ubuntu did not fix anything.


I am now left with grub menu at bootup time. 


Ran bootinfo utility ( from persistent USB stick) and the report is at [https://pastebin.com/bSdFX5Fx](https://pastebin.com/bSdFX5Fx)




Can anyone help in reviewing and suggesting a fix ?


thank you in advance,
Raj.

---

### Post by oldfred on 2017-06-16
You have UEFI hardware and Windows installed in UEFI boot mode.
But you installed Ubuntu in the 35 year old BIOS boot mode.
The two modes are not compatible, and you cannot dual boot from grub. But may be able to dual boot from UEFI boot menu. You may have to turn on or off UEFI or BIOS to boot in correct mode to match install.
Better to have Ubuntu in UEFI boot mode, and Boot-Repair's suggestion is to do that.

But it looks like you have run Boot-Repair a lot of times and have many copies of /boot-sav folders in the ESP - efi system partition or sda1, so no more room to install Ubuntu/grub2's boot files for UEFI boot.

Turn off Windows fast start up in Windows.
Then houseclean all but last one of /boot-sav folders in sda1.
Then use Boot-Repair to reinstall grub in UEFI boot mode.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

See also link below in my signature.

---

