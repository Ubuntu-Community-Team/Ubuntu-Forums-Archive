---
title: "The reboot after installation gives nothing"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by zlotz2 on 2018-02-14
Hello everyone

I'm trying to leave Windows 7 for Ubuntu on my desktop.

I've created a bootable USB drive with Etcher on my netbook (which is under Ubuntu already).

The installation of Ubuntu 16.4.1 (or 16.4.3 or v14 or Mint or other distributions) seems to take place correctly.
When I reboot the computer, I get the following menu :
- Ubuntu
- Advanced options for Ubuntu
- Memory test (...some stuff...)
- Memory test (...some stuff...)
But, when I choose Ubuntu (or wait until it runs by itself), the screen remains black with only a blinking cursor on top left.

I've tried to remove successively the options nomodeset, acpi=off, noapic, with the same result.

This problem has been lasting quite a long time and I really don't want to go back to Windows.

Here is a description of my hardware :
[HTML]description:     Desktop Computer
product:     System Product Name (SKU)
vendor:     System manufacturer
version:     System Version
serial:     [REMOVED]
width:     64 bits
capabilities:     smbios-2.7 dmi-2.7 vsyscall32
configuration:    
boot    =    normal
chassis    =    desktop
family    =    To be filled by O.E.M.
sku    =    SKU
uuid    =    [REMOVED]
id:    
core
description:     Motherboard
product:     P8Z77-V LX2
vendor:     ASUSTeK COMPUTER INC.
[/HTML]

Here is my boot-info :
[http://paste.ubuntu.com/=W276mcn6j6/](http://paste.ubuntu.com/=W276mcn6j6/)

If it can help, some guy told me that it was not normal that the grub.cfg was on read-only in the following situation :
[HTML]ubuntu@ubuntu:~$ sudo   mount   -v   /dev/sda1 /mnt
mount: /dev/sda1 mounted on /mnt.
ubuntu@ubuntu:~$ cd /mnt/boot/grub
ubuntu@ubuntu:/mnt/boot/grub$ ls -l
total 2384
drwxr-xr-x 2 root root    4096 Feb  7 22:33 fonts
-rw-r--r-- 1 root root     712 Jul 19  2016 gfxblacklist.txt
-r--r--r-- 1 root root    8479 Feb 10 11:19 grub.cfg
-rw-rw-r-- 1 root root    1024 Feb  7 22:33 grubenv
drwxr-xr-x 2 root root   12288 Feb 10 11:19 i386-pc
drwxr-xr-x 2 root root    4096 Feb 10 11:19 locale
-rw-r--r-- 1 root root 2398585 Jul 19  2016 unicode.pf2[/HTML]

I will bless any person helping me to unblock this situation.
Thanks.

---

