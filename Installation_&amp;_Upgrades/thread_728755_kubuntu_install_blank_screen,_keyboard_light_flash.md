---
title: "kubuntu install blank screen, keyboard light flashing"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by gdf1y on 2008-03-19
Hi!

Trying to install kubuntu-7.10-desktop-amd64, but after I select an option from the initial install boot screen I get blank screen and keyboard CAPS LOCK light flashing. Tried noapic nolapic pci=noacpi acpi=off options but no result. Maybe there's a problem in my hw configuration?

Here's my config:
AMD Athlon 64 3200+
Mainboard DFI Lanparty (nForce 4 ultra-d)
Video Saphire ATI x800 gto
1 pata + 2 sata hdd's with NTFS partitions (would format one during install)

Please, can you help me. Searching hasn't solved my problem.

Thx

---

### Post by Peter09 on 2008-03-19
Turn off the quiet swith in grub. It may show you where the boot is failing.

PC

---

### Post by petatkinson on 2008-03-19
90% sure its a bad cd/dvd media burn.Try re-burning the media and reinstall.Failing this its video drivers that are the problem

---

### Post by gdf1y on 2008-03-28
Thanks for help. Turned off "quiet" and "splash" parameters in grub and could see the error: "...please append a correct "root" boot option...".

Ading parameter root=/dev/sdb2 allowed me to boot, though the chance of successful boot was like 30%. Sometimes another parameter worked: root=/dev/hdb2 (d.k. why the same parameter could work this time but not the next time I boot)

After install I had to edit /boot/grub/menu.lst removing parameter "splash" as this was causing kernel freeze.

---

