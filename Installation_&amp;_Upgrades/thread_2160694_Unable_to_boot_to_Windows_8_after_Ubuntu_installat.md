---
title: "Unable to boot to Windows 8 after Ubuntu installation on new dell laptop"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by anoop2811 on 2013-07-07
[COLOR=#000000][FONT=arial][FONT=arial][COLOR=black]Hi,   I installed Ubuntu 13.04 on my new WIndows 8 Dell laptop following the instructions in the forums. I did the following:
1. Disabled Secure boot in UEFI
2. Shrunk my only partitioned drive and created an unallocated 100 GB.
3. Created LiveUSB
4. Booted from LIve USB and installed Ubuntu 13.04 (had a power outage in between but was able to reinstall after starting up)
5. Installed boot-repair and run the same.


However there was not Windows 8 boot option in the grub menu. After looking up some forums, manually added an entry in the 40_custom file in grub.d. However though now I see the option for WIndows 8 based on the menu entry I made, am still not able to boot into it. Any help appreciated.




The link that showed up on running the boot repair is : [http://paste.ubuntu.com/5845526/](http://paste.ubuntu.com/5845526/)


I have a dell inspiron 15r laptop 5521 which came preinstalled with windows 8.


[/COLOR][/FONT][/FONT][/COLOR]

---

### Post by Penguenci on 2013-07-07
Sounds like a drive mapping problem to me. UEFI is tricky, but let me tell you how to solve the problem on a BIOS system. I'd say it has a 51% chance of taking care of your issue as well, now that you've come thus far.

Install GRUB Customizer, it's a must for dual booters using any Linux distro. On the very first menu that greets you as you open it, find the Windows 8 Loader in the list. Right click on it and choose Edit. You'll probably see that the way your Windows 8 loader is handled is set to "Other". Change that into ChainLoader, save your settings and reboot.

---

### Post by Cyberz on 2013-07-08
try install [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/) in linux.
then make sure boot is set to that disk in bios.
it fixed my problem

---

