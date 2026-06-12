---
title: "Grub isn't detencting Windows 7."
date: 2015-09-07
forum: Installation &amp; Upgrades
---

### Post by gerardo10 on 2015-09-07
Hello guys. I've using Gnome for the last few months and I totally love it.

I have two hard drives, one for Windows 7 & the other one for Gnome. I can boot into Gnome with no problems but when I try to boot into windows my Grub seems to not detect Windows. I cant even boot windows from the BIOS, it just pops a "Searching boot files" screen & sends an error that it didn't find the files and starts again in a eternal loop.
I don’t think my Windows drive is damaged because I can fully manipulate it from Gnome.
The only way I found to boot Windows is by unplugging the Gnome drive and, as you can assume, don't want to be unplugging the drive every time I want to use Windows.

I have tried "sudo update-grub" and adding an entry to my menu list but nothing seems to work.

This is what "sudo update_grub" gives back:
[B][I]Generating grub configuration file ...
Found background image: background.png
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-22-generic
Found initrd image: /boot/initrd.img-3.19.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-20-generic
Found initrd image: /boot/initrd.img-3.19.0-20-generic
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done[/I][/B]
As you can see no Windows 7 entry.

Thanks, looking forward to solving this problem.

---

### Post by ajgreeny on 2015-09-07
See Boot-Repair in my signature and run that to get the Boot-info report, then post back here the pastebin link and someone will probably be along to tell you what it means, and how to solve the difficulty.

Could this be a BIOS vs UEFI problem?  If so the report will tell us.

---

