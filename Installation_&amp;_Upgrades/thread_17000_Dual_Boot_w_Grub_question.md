---
title: "Dual Boot w/ Grub question"
date: 2005-02-25
forum: Installation &amp; Upgrades
---

### Post by Skywing on 2005-02-25
hey, im currently dual booting Fedora Core 3 and Windows on my thinkpad, at the moment im using GRUB to select what OS i wanna use, now, id like to get rid of fedora and try ubuntu out, is it just a matter of booting of the CD and having the installer wipe the fedora partition? will it replace my current bootloader for its own?

---

### Post by thestarman on 2005-02-25
[QUOTE=Skywing]hey, im currently dual booting Fedora Core 3 and Windows... using GRUB to select what OS i wanna use, now, id like to get rid of fedora and try ubuntu out, is it just a matter of booting of the CD and having the installer wipe the fedora partition? will it replace my current bootloader for its own?[/QUOTE]

That's essentially it.  Ubuntu uses GRUB too, by the way, but let it overwrite the old version in your MBR sector so it will point to the new stage2 code sector in Ubuntu instead of the old sector from FC3!  Also, Ubuntu's install should add your Windows OS to its menu by itself; it did for me... it even added my RedHat9 OS to the list!

The Starman.

---

