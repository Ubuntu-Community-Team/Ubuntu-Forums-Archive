---
title: "[SOLVED] Kernel Panic: not syncing to IO-APIC"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by BobLand on 2008-02-11
I have a brand new AMD 64 x2 dual core 5200+.  I just got XP installed and now trying to install Gusty.  I can't get pass this error which occurs as soon as I hit the Install... (first line).  I went to the bios and tried different settings.  None had a noapic option.

I am using both graphic and alternate versions of 7.10.  I know the disks are good because I used them both to install on disk in another system which is a pentium 4.

I've heard that the 64bit version has more problems then it's worth at this point.  I just want to get the machine up and running as it's for my wife's business.  Right now, she's using my machine (Gutsy) so I'm locked out of my work.

I'm not thrilled that I have to create this entry using XP.

Any help appreciated.
bobland

---

### Post by BobLand on 2008-02-11
Fixed.  After searching various forums the problem was easily solved by restoring the defaults to the bios and then disabling ACPI APIC Support.  Booted to the LiveCD and installed just fine.

Rebooted a number of times just to make sure and the system is stable and up and running.

Hope this helps someone.
bobland

---

