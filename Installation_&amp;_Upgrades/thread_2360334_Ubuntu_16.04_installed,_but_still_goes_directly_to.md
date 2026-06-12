---
title: "Ubuntu 16.04 installed, but still goes directly to Windows"
date: 2017-05-03
forum: Installation &amp; Upgrades
---

### Post by cyandris on 2017-05-03
[COLOR=#111111][FONT=Ubuntu]I tried to dual-boot ubuntu 16.04 alongside Windows 10 on my Acer laptop. [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]After installation, I go directly into windows.

Things I've tried:
[LIST]
[*]Turning off Fast Startup and Secure Boot
[*]Boot repair
[/LIST]

I ran Boot-info and received the following report: [/FONT][/COLOR][https://paste2.org/7n5F1bZv](https://paste2.org/7n5F1bZv)

[COLOR=#111111][FONT=Ubuntu]I have no experience with Unix, and have no idea what is wrong with GRUB. Any help with why Ubuntu won't boot would be much appreciated.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]

---

### Post by WMDwebs on 2017-05-07
check bios for boot order...need to get to GRUB to change boot OS

---

### Post by ubfan1 on 2017-05-07
I think in Acers, you have to set a supervisor password in the UEFI settings (formerly known as BIOS).  Then you need to set "trust" on the Ubuntu bootloaders shimx64.efi and grubx64.efi.  With trust, you should be able to use efibootmgr to add the ubuntu entries to the bootorder, the entries already exist, but they are not in the bootorder (line 774 of your boot-repair link).  You might be able to actually boot ubuntu now just by using the EFI boot selection (some function key at power-on), and select ubuntu (or maybe hard disk, then Ubuntu).

---

