---
title: "Can't access grub after windows update. Automatically boots to Windows."
date: 2020-04-22
forum: Installation &amp; Upgrades
---

### Post by jamesoreilly on 2020-04-22
Windows forced an update and I can no longer access grub and therefore can't access my Ubuntu partition. Computer automatically boots to Windows and I cannot find a boot option in the BIOS that opens grub when I reboot.

I have tried using BootRepair with Ubuntu on a USB drive, but it has not worked and there is no boot option to access grub.

Here is a link to a pastebin with the BootRepair info report: [http://paste.ubuntu.com/p/JJkkrr6cJW/](http://paste.ubuntu.com/p/JJkkrr6cJW/)

I have a coursework due tomorrow which I need to do with Ubuntu so this timing is pretty unfortunate for me. Any help is greatly appreciated.

Cheers, 
James

---

### Post by jamesoreilly on 2020-04-22
SOLVED

Had to change the bootloader in windows, using the command suggested in the Bootrepair summary.

---

