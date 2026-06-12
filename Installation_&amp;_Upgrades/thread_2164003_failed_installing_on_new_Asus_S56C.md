---
title: "failed installing on new Asus S56C"
date: 2013-07-20
forum: Installation &amp; Upgrades
---

### Post by levengli on 2013-07-20
I have a new Asus S56C laptop which came preinstalled with Windows 8. The graphics card is Nvidia GeForce GT 740M.
I am facing the infamous issue where I am unable to install Ubuntu due to a black screen. 
[LIST]
[*]I am trying to so so with UEFI enabled, Secure Boot enabled and Fast Boot disabled. 
[*]I am trying to install 13.04 TLS 
[/LIST]
Based on [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535), I tried running with ```
nomodeset acpi_osi=Linux nosplash --verbose text
``` (all but the *nosplash *placed after the original closing *--*). I also tried replacing *nomodeset *with *xforecevesa*. However, this all failed and I am still unable to see anything after I try installing Ubuntu from the Grub menu.

(Unrelated?) Note: I once tried installing with Secure Boot disabled and saw the error: "kernel panic VFS: unable to mount root fs on unknown-block (0,0)"

---

