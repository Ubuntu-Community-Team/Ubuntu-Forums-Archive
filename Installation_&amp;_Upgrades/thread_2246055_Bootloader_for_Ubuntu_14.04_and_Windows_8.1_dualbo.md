---
title: "Bootloader for Ubuntu 14.04 and Windows 8.1 dualboot"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by lorenz2 on 2014-09-28
Hi,

I'm trying to set up a dualbooting windows 8.1 and ubuntu 14.04 machine. I've installed the two OSs in different orders, but in either case I can only boot into windows. 

I tried reinstalling ubuntu, reinstalling grub from a live cd and ran boot-repair from a live cd (ubuntu 14.04) without success. Here is the boot-repair system info [http://paste.ubuntu.com/8445646/](http://paste.ubuntu.com/8445646/)

I'm guessing that something with the EFI settings is wrong, but I don't really understand this. I would be very grateful for some help ;)

Thanks for your help!

---

### Post by lorenz2 on 2014-09-28
Just solved my problem, sorry for the unnecessary post. Here's what I did: 

start windows
use command line
type "bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi" (without quotation marks)

If I understand correctly this sets the EFI configuration to use the specified bootloader. From the grub menu I can then choose to boot into the windows boot menu.

---

### Post by oldfred on 2014-09-28
That is one of several work arounds for systems that only want to boot Windows.

I believe that setting has Windows change the boot once efi setting to ubuntu and then reboots.

There are several other work arounds which you can try if you like. Renaming bootx64.efi or using rEFInd seem to be two of the others that work best.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order](http://askubuntu.com/questions/507013/windows-8-1-changes-boot-order)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

