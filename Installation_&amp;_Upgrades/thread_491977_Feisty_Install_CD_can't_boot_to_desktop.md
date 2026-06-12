---
title: "Feisty Install CD can't boot to desktop"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by lancest on 2007-07-04
Toshiba L20 updated bios
Feisty Live cd won't boot to desktop. Just hangs after install screen
This laptop worked well before on Linux before Toshiba changed the board.
Getting message something like: MP-Bios 8254 timer not connected, bug in init detected
Is this an ACPI problem?
Is this where I need to do something like: acpi=off as a kernel parameter?
What should the command look like?

---

### Post by wpshooter on 2007-07-04
Did you have Ubuntu installed on the hard drive that was on this system BEFORE the motherboard was changed ?  It sounds like you did.

If that is the case, if it were me and there was nothing on the hard drive installation that I needed to keep, I would get [www.killdisk.com](www.killdisk.com) and I would wipe the drive completely clean.  Before you do that might not be a bad idea to go into the BIOS and reset everything to defaults and then change and BIOS parameters as adviseable.  Then reinstall Ubuntu from scratch.

---

