---
title: "Server install on a usb stick, grub fails"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by MatBi on 2006-06-22
I'm trying to install ubuntu on a 2 Gb memory stick. I use the server version because the others require more than 2 gigs. 
At first i tried with the standard installation; Grub fails with error 18 upon reboot.
I also tried with lilo: booted from cd, chrooted to usb stick, and installed lilo. Upon reboot, lilo get stucks, the last message being "Uncompressing Linux... Ok, booting the kernel."
I don't know what is left to try, anyone can help?

MatBi

---

### Post by rcarring on 2006-06-22
Try installing grub to a floppy. Have you got legacy support enabled for your usb devices in the bios?

---

### Post by bamarob on 2006-06-22
I'm having very similar issues.  See my thread here: [http://www.ubuntuforums.org/showthread.php?t=201899](http://www.ubuntuforums.org/showthread.php?t=201899)

Hopefully, someone with more experience than I will respond.

BR

---

### Post by MatBi on 2006-06-22
[QUOTE=rcarring]Try installing grub to a floppy. Have you got legacy support enabled for your usb devices in the bios?[/QUOTE]
Unfortunately i have no floppy; in the bios there's no "legacy support" option. My mobo is an EPIA ME6000.
I just tried also to install to an external hdd; at the first boot grub says "error 18" and goes no further.
I'll try now Breezy, following this promising howto: [http://ubuntuforums.org/showthread.php?t=80811]("http://ubuntuforums.org/showthread.php?t=80811")

---

### Post by MatBi on 2006-06-23
Update: no luck even with Breezy, i get the same "Error 18". 
I'm stuck.

---

