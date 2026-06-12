---
title: "Unable to generate grub (with boot-repair or super-grub2)"
date: 2017-04-01
forum: Installation &amp; Upgrades
---

### Post by juanfe2 on 2017-04-01
[FONT=arial]Hello! I want to dual boot win10 and ubuntu. I have some problems with boot-repair. It does not repair the boot problem, or generates de grub, so when i restart, i am on windows and not in the grub.[/FONT][FONT=arial]
[/FONT]
[FONT=arial][http://paste.ubuntu.com/24295209/](http://paste.ubuntu.com/24295209/)
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Boot-repair also said to make my bios boot in sda1/EFI/ubuntu/shimx64.file, but i have no idea how to do it or where to find this file (if it is in ubuntu or windows). The only way to get into Ubuntu is with a bootable usb with super grub2 on it, and i have tried some things in the terminal but nothing works, always a problem, always searching what is happening, always getting into new problems.

I am searching on google and in the forum, but i would really appreciate some help. I am new on Ubuntu and is kind of overwhelming.

I know there are some posts about it, i read some, but i am having problems with ubuntu for one week, and i'm really exhausted.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thank you very much[/FONT]

---

### Post by oldfred on 2017-04-02
It looks like you have an Acer. And Acer has a unique requirement of setting an UEFI supervisory password (never lose that, or erase after configured) and enabling "trust" from within UEFI on the Ubuntu/grub .efi boot files.

Also some threads mention downgrading UEFI. But newer ones say the newest UEFI from Acer works. So make sure you have newest UEFI from Acer.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
[/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 

[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by juanfe2 on 2017-04-03
Thank you very much oldfred! It's not a dual boot, but is better than nothing. Damn Acer!

---

### Post by oldfred on 2017-04-03
You still have to set trust.
Do not know if the Windows boot file has trust or automatically has trust set.
If it is automatic and you are only booting Ubuntu you can create the Windows file in the Microsoft efi folder but make it actually be shimx64.efi.

That was a common work around, but with dual boot systems, Windows often updates to its file and then work around has to be redone.
Most not use the fallback entry if dual booting. That is /EFI/Boot/bootx64.efi which again we make actually be shimx64.efi. Every system should boot that file as that also is how all UEFI external drives are booted. It just that it also works now for internal drives.

---

