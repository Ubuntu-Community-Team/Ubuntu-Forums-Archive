---
title: "edgy live cd hangs at boot after init-premount on AMD system"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by lucnoc on 2006-11-08
Hi,

When booting the edgy live CD I can't get passed the graphical screen. 
(I used that same cd on another machine and it worked fine.)

Editing the boot command (by typing F6) and removing quiet and changing splash to nosplash the computer hangs at:

Begin: Running  /scripts/init-premount ...
[17179572.184000] ACPI: Fan [FAN] (on)
[17179572.188000] ACPI: CPU0 (power states C1[C1] C2[C2]
[17179572.188000] ACPI: Thermal Zone [THRM] (40 C)

I had Dapper (as the only OS) working fine on this PC:
AMD Athlon XP 2400+
ATI radeon

I tried the non live cd and after installation it hangs at a similar place right after the graphical ubuntu screen comes-up.

I also tried to add to boot params (noapic pci=noacpi acpi=off nolapic irqpoll...) without success. 

Any suggestions on what I could try next?
Cheers,

-Luciano

---

