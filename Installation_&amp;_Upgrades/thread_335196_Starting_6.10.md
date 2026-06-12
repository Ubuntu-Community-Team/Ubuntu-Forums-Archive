---
title: "Starting 6.10"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by newaustralian on 2007-01-10
As someone new to Ubuntu I thought I would start with version 6.10. Download and writing of CD went OK.  Checksums fine.  Booting from CD fine.  Using CD to check itself fine.

So I went for the graphical install from the CD with high hopes.  loading kernel OK, check of files OK, "mount " disabled.  Golden brown screen appeared with arrow cursor in center.   CD spun for a few minutes then stopped.  Nothing else happens, system appears hung.

Would appreciate help. Any ideas.

---

### Post by meng on 2007-01-10
Still could be a bad burn. Consider reburning at a slower speed. Otherwise consider downloading and installing the Alternate CD rather than using the Live one.

---

### Post by newaustralian on 2007-01-11
Many thanks for advice. I tried slower burn but still same result. I now have two disks which pass the integrity check but will not complete the start. A large amount of the disk is read in judging the time the drive spins but the system just hangs.  Have tried the start mode and the graphical safe start mode but same result.  

I want to stay with the live CD so I can try linux as a first time user.

System is a 1.3 Celeron with 256 SDRAM and IntelDirect AGP.

Any more thoughts anyone.

---

### Post by penvzila on 2007-01-11
There should be a boot option with things like "noacpi, noapic, nolapic,.."  Try using that.  I've had to do this with the new Edgy install cd on all my installs.

---

### Post by newaustralian on 2007-01-11
Many thanks. It worked. I escaped from the default graphic boot and at the boot prompt typed "live acpi=off apic=off lapic=off" and bingo.

Enjoyed looking at the examples and trying the apps.  Congrats to the development team.:D

---

