---
title: "Install Doesn't Finish"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by macogw on 2007-03-21
I'm trying to install Edgy on a computer at work.  With the live cd I needed "safe graphics mode" because of nVidia, but it got to 73% and froze completely (have to reboot) twice.  I checked the md5 and it's fine.  I downloaded the alternate install disk and checked the md5, burned it, and tried.  It froze at 94%.  I did the "check cd" option to make sure it wasn't a bad burn, and it said it was fine.  I tried twice more and it froze at 94%.  I looked at what package it freezes on, and it freezes on acpi.  Is there a way I can make it install without that?  It's a desktop, so it's not like we have to worry about battery life or anything.

---

### Post by Kateikyoushi on 2007-03-21
Boot from the cd at the menu press F6 then press E to edit the startupline and add add these options to the end of the line.

noapic
nolapic
acpi=off

---

### Post by macogw on 2007-03-21
Will that also affect the installation?  I thought those options only stopped them from loading during the bootup of the cd.

---

