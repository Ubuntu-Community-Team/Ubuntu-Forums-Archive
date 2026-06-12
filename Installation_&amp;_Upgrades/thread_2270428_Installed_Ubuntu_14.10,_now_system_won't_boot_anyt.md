---
title: "Installed Ubuntu 14.10, now system won't boot anything"
date: 2015-03-22
forum: Installation &amp; Upgrades
---

### Post by Mike_Ohlhausen on 2015-03-22
I installed Ubuntu 14.10 to an Intel SE7520BD2SATA2 server board, adding in ssh, LAMP, postgre-sql, and Samba. cleared all drives completely, and switched all of them to gpt partitions, and using btrfs formating. The drives are 2 Sata 30 gb on the board's controller, 1 80 gb (pata) on the board, and a dvd to load from as a slave. There are 8 other drives as data drives on an old 3Ware 7800 controller (ide drives). I have been testing to get an operational system before the larger sata drives get here, but have been pretty much unsuccessful. I did have it once where I could use putty from the windows machine to work on it, but could not get the video to work from the Ubuntu machine. When I reinstalled it this time with the other drives, I wiped everything, for a 'clean' install. Bad plan, the machine reboots, and I have a blinking curser, and nothing bootable, not even the dvd, so I can't even retry Ubuntu, or try to fix it. Scratching my head... No windows or dos will be on this. I did use Gparted to wipe it all, and switch to GPT, then booted the Ubuntu 14.10 which all seemed fine until it rebooted, or didn't. Any thoughts? This is an early EFI board, and I have heard Ubuntu might have a problem, but thought it was fixed. Also there is the thought that Grub was 'updated' during the install removing the grub-efi-64... (sp?) still, I can't get in to fix it.

---

### Post by Mike_Ohlhausen on 2015-03-24
Ok, not really fixed, (Or rather, I kermudged it, and don't know exactly what I did) but I did get it to boot from the DVD once again. Just from jacking with settings in BIOS, looking for something that might make it mess up, and rebooting with a different boot disk each time. No one thing seemed to work, so I missed the one thing that worked. If that makes sense. I changed boot order, and tried settings to defaults, (then fixing them afterwards) removed half the ram, removed a SATA BluRay burner, switched the boot drive, then put it back again... etc. At any rate, it finally booted the Ubuntu Server 14.10 disk again, and I re-installed.  I have searched for a command to make sure I have the correct Grub, but cannot find it. there seems to be an update that replaces grub-efi-64 (sp?), and it shouldn't? I noticed the installer took off on it's own this time, and did updates...

---

