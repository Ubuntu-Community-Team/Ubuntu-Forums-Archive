---
title: "ubuntu clean install wont boot"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by tetsu7 on 2011-12-17
did a clean install of ubuntu 11.10 x64 on a 1TB sata hitachi hdd. it is booted alone. theres nothing else on the drive. couldnt boot the operating system it said "error: out of disk" so i did a clean install again but same thing. after rebooting enough the OS booted so i reinstalled grub via terminal. did a bunch of work getting my lamp and ftp server up etc. rebooted and my mobo boot screen was locking up so i checked the mobo code which said "initializes IPL devices controlled by BIOS and option ROMS" which i think means my problem lies with the boot strap. i threw in super grub disk 2 and it seems to find a grub image but when i try to boot it i get "error: hdo, 1 out of disk error: you need to load the kernel first." i tried booting from livecd and chrooting my way to a grub purge and install on /dev/sda via this guide [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) only to reboot with "error: hd0 read error" and a grub rescue prompt. any ideas how i can fix this please?

EDIT: ok so i switched sata ports on my barley 2 month old mobo and it seems to boot every time..ill have to remember this one lol

---

