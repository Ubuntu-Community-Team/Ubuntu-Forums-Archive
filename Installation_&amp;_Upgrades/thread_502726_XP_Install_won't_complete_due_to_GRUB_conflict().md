---
title: "XP Install won't complete due to GRUB conflict(?)"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by davidsiegel on 2007-07-17
[LEFT]Disclaimer: I'm only installing XP to empathize with my Windows-using friends as I help them transition from Windows to Ubuntu. Oh, and I need to configure my AirPort Express.

I'm trying to install Windows XP on my first partition (/dev/sda1) while Ubuntu is already located on /dev/sda4. The XP disc boots and copies the "WINDOWS" folder to the first partition, which I previously formatted as NTFS. Then the computer reboots after the XP installer copies the necessary files and all I get is a black screen with an underscore in the upper left-hand corner. I used the Super Grub CD to re-install GRUB over the failing Windows bootloader to get back into Ubuntu and run update-grub to re-write my /boot/grub/menu.lst file, to which I added the directives to make booting Windows XP an option in GRUB. All of this works, except when I select Windows to boot at the GRUB menu, I just get a black screen with the underscore. I have a feeling the XP installation didn't finish because it didn't successfully reboot after the initial installation phase due to a bootloader conflict. I'm really unsure of the nature of my problem, though, because I am not a Windows user! Windows users, what is going on here? How does the XP install work and is it conflicting with GRUB? How can I successfully install and boot XP?
[/LEFT]

---

