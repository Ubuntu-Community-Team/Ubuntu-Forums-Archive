---
title: "ubuntu uefi boot not working (windows 8.1 uefi preinstalled)"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by morgan9 on 2014-06-10
[SIZE=2][FONT=arial]I installed ubuntu 14.04 via a bootable usb drive to a new laptop, an [/FONT][/SIZE]acer v5-573p-9899.  Grub is not being displayed at boot time, it goes straight to Windows.  

[SIZE=2][FONT=arial]I then disabled fast boot/secure boot in Windows 8.1.  I attempted to run boot-repair as directed at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  I tried the recommended settings, which did not work, then I tried again with an advanced configuration - no change. This is the link I was supplied at the end [http://paste.ubuntu.com/7624239/](http://paste.ubuntu.com/7624239/)[/FONT][/SIZE][FONT=arial][SIZE=2][FONT=arial] (it did not fix the problem, grub does not load at boot up, instead boots straight into Windows)[/FONT]
[/SIZE]
[/FONT]

---

### Post by ubfan1 on 2014-06-10
The last efibootmgr output you posted does look like ubuntu (grub) is first in the boot order.  Can you invoke the efi boot menu (some function key usually at power on), which gives you boot choices for devices and maybe OSes?  If you select ubuntu, do you get grub?  You have secure boot off now correct?

---

