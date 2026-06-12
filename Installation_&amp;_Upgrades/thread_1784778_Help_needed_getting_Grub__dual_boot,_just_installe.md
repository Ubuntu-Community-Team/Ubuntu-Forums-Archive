---
title: "Help needed getting Grub / dual boot, just installed Ubuntu"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by Beowulf.1000 on 2011-06-17
I just installed Ubuntu 10.10 x64 to my desktop. I need to somehow get it working so during boot I see Grub showing me the option to boot into Ubuntu or into Windows 7. 

Ubuntu is on a PATA (ATA) drive, /dev/sda, first drive in the BIOS boot order listing.

Windows 7 x64 is on SATA drive, /dev/sab, second drive in the BIOS boot order listing

I do not see any Grub menu whatsoever when my computer boots, it just boots automagically into Ubuntu. I want o get Grub installed on /dev/sda (PATA drive with Ubuntu. Leave my Windows 7 /dev/sdb drive alone, no Grub on it).

I have used Grub in the past, used to have the option to install it during the installation of Ubuntu but I do not recall seeing that during the install today of Ubuntu 10.10 off a live CD.

Any help appreciated, I would certainly like to get my PC working so I can also boot into Windows 7.

---

### Post by Quackers on 2011-06-17
Open a terminal in Ubuntu and run ```
sudo update-grub
``` and watch as grub.cfg is configured. Does it pick up the Windows Loader?
If it does, reboot and you should get a grub menu.

---

