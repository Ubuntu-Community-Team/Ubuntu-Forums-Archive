---
title: "Ubuntu 12.10 Desktop and Windows 8 Dual Boot issues"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by TrevyBell on 2013-03-18
Hello, recently I installed Ubuntu 12.10 desktop to my laptop,(which came pre-installed with windows 8). When I installed ubuntu I chose the option for it to boot alongside windows 8, ever since however, I get an error when chooing to boot windows 8(or its recovery option) where it simply says 

[LIST]
[*]error: can't find command drivemap. 
[*]error: invalid EFI file path               . Any Ideas/help for me? 
[/LIST]

---

### Post by oldfred on 2013-03-18
Did you install in UEFI mode?

Even if in UEFI mode grub2's os-prober only creates BIOS mode chain entries which do not work with UEFI.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

