---
title: "system hangs occasionally on ubuntu 9.10. keyboard and mouse does not respond at all."
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by santy118 on 2010-04-21
Hi,

I am running ubuntu 9.10 on a HP desktop. I switched from winXp to ubuntu 9.10 2 months ago. I am running into a peculiar problem since 2-3 weeks. My system hangs occasionally. Keyboard and mouse does not respond at all. I had to do a hard reboot. I have noticed few things repeatedly when it happens. 
- when my thunderbird email alert is displayed. that too some times, not always. 
- While using eclipse, On mouse hover on a my code, i get some info message. 

My dmesg says this


[    0.529597] ACPI Error (dsfield-0140): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.529608] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013420), AE_ALREADY_EXISTS
[    0.529647] ACPI Warning: \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 20090521 nspredef-328
[    0.529817] ACPI Error (dsfield-0140): [CAPD] Namespace lookup failure, AE_ALREADY_EXISTS
[    0.529826] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0._OSC] (Node f7013420), AE_ALREADY_EXISTS
[    0.529854] ACPI Warning: \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 20090521 nspredef-328
[    0.529884] pciehp: PCI Express Hot Plug Controller Driver version: 0.4


Any help in this regard is highly appreciated. 

Thanks
Santy

---

