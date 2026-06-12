---
title: "live cd will not boot"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by alandowning on 2005-07-01
Completely new to Linux,got the live CD today and tried to boot from it just to see what Ubuntu was like,it booted from my Cd drive to the first screen asking me to press Enter to continue the boot up.But the screen just kept recycling between my bios screen and the first Ubuntu screen.What am I doing wrong. ](*,)

---

### Post by mingus on 2005-07-01
[QUOTE=alandowning]Completely new to Linux,got the live CD today and tried to boot from it just to see what Ubuntu was like,it booted from my Cd drive to the first screen asking me to press Enter to continue the boot up.But the screen just kept recycling between my bios screen and the first Ubuntu screen.What am I doing wrong. ](*,)[/QUOTE]

The most common problem is with the CD media itself.  You can do an md5 check to verify it's integrity.

Or it can be a problem between the Linux kernel and your hardware (how long after you hit Enter does it recycle?).  The following turns off some of the more common conflicts:

:live acpi=off noapic nolapic nodma video=vga16:off

there should be a colon between "vga16" and "off" - blasted web page puts a smiley there when a colon gets typed

---

