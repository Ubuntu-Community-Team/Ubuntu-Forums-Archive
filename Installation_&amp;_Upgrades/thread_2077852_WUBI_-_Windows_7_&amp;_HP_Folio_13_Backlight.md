---
title: "WUBI - Windows 7 &amp; HP Folio 13 Backlight"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by omicronkappa278 on 2012-10-29
I am attempting to install Ubuntu with WUBI. The HP Folio 13 has a backlight problem with Ubuntu. Normally if you install it to the laptop by itself, you can hit SHIFT on boot and add acpi_backlight=vendor and then edit Grub and you are good, Not here. Once WUBI is installed and I hit SHIFT on boot, I have no option to put the acpi_backlight=vendor phrase anywhere. Anyone had this issue? I cannot See UBUNTU when it boots up.

---

### Post by Mark Phelps on 2012-10-29
Since Wubi does not use the standard GRUB code, it doesn't create the same directories; instead, it creates directories in the Windows filesystem.  It uses a GRUB derivative called GRUB4DOS -- but it might end up using the same config files and parameters as the regular GRUB.


Sorry, not a Wubi expert -- but you could look through the Windows filesystem for a GRUB config file.  Might be in the wubildr or GRUB4DOS directories.

---

### Post by bcbc on 2012-10-30
Once wubi is installed it's the same as for a normal install.

When you see the grub menu, hit 'e' to edit the first entry. 

If you don't see the grub menu, hold down the SHIFT key after selecting Ubuntu (from the Windows boot manager).

---

