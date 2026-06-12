---
title: "Installation problems continue..."
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by ulikhan9 on 2006-10-23
I have two sata drives. One 80gig with windows xp, one 250 gig unallocated free space.  I have tried knoppix cd and ubuntu cd. Both cds are error free, they both get to 100% loaded stage, then my computer freezes.  The screen goes black and Im left with a cursor that eventually disappears.  I have successfully loaded xp on the 2nd sata drive no problems. Why wont the linux cds work. Can anyone think of a hardware or software problem that is preventing my from even trying this os?

Setup - Asus a8v board, athlon 64 3000+ cpu, 1gig ram(checked, its fine), ati radeon 9600 card, 2 sata drives, bluetooth keyboard & mouse, liteon dvd burner, and a partridge in a pair tree.:confused:

---

### Post by Kateikyoushi on 2006-10-23
Try to boot with these options it might help.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

