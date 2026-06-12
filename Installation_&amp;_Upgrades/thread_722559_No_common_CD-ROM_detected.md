---
title: "No common CD-ROM detected"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Bonanzaman on 2008-03-12
OK, I'm hoping someone has come up with somthing for this as the last 2 threads on this subject I looked at have been dead-ends! After plugging in some boot parameter commands, I got the alternate CD to boot up, and after the location and keyboard questions, I get a failure to detect any CD-ROM drive (even though the darned thing just booted from the CD-ROM!!). 

Checked Puma's previous suggestion on an old thread, about making sure the CD-ROM is set as secondary master, leaving bios as "auto", and setting the cd 1st in the boot order. Tried setting my DVD Drive the same way, but cannot get a boot from it at all.

Dell Dimension 4100
Intel i815 / PIII/ 996Mhz
20GB Maxtor HD
384 Meg Ram
Lite-On LTN486 48X CD-ROM

Could this be a driver issue, or do my bios settings need tweaking? or..................?

---

### Post by Pumalite on 2008-03-12
What are the choices you have in your BIOS for CD. If you have AHCI, maybe that's the one you should choose. You have to look in 'IDE Configuration' and look at CD.

---

### Post by Bonanzaman on 2008-03-12
Thanks, Puma....my choices are:

None
User
Auto    (current setting)
CD-Rom  (tried previously)
ATAPI Removeable
Other ATAPI
IDE Removeable

---

