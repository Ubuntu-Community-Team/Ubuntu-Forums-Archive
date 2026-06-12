---
title: "Boot problems with repacked Ubuntu iso"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by Bezimeni on 2014-01-31
Hi guys I downloaded the 12.04 LTS today and wanted to add manual (getting started with ubuntu 12.04) to the disk so I unpacked (with 7z) and repacked the iso (with iso-creator) in win 7. Everything seems fine in Windows and I can run the installer and all normally. However when I restart my computer to boot Ubuntu from disc it won't start and simply goes straight to Windows even though the boot order is correct. Something must have gone wrong with repacking the iso. Unaltered iso I downloaed last year boots fine. Any ideas how to repack the iso so it works as a bootable live dvd?

---

### Post by grahammechanical on 2014-01-31
Unpack and rebuild the ISO image from Ubuntu and not Windows. Is that worth a try? What changes has that Windows application made to the scripts in the ISO image so that the computer boot system (BIOS/UEFI) does not recognise that an OS is on the disk?

Regards.

---

### Post by Bezimeni on 2014-01-31
When extracting with 7z [Boot] folder with Bootable_NoEmulation.img is visible now unlike when I open it with virtual device. I guess that's the problem. How to repack the ubuntu without messing this up. Its probably should be easy but I haven't done it before. p.s. I don't have any linux distros currently installed on this computer.

Edit: solved, just use some iso editing software that allows you to add new files into it i.e. WinIso. It works.

---

