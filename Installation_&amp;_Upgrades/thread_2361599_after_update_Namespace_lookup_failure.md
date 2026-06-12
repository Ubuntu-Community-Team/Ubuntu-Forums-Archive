---
title: "after update Namespace lookup failure"
date: 2017-05-18
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2017-05-18
Hi
After updating from 16.04 to 17.04 I get this. What is that?
Thanks

[    1.143757] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20160930/psargs-359)
[    1.143792] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT2._GTF] (Node ffff93b2ce0e71e0), AE_NOT_FOUND (20160930/psparse-543)
[    1.143852] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20160930/psargs-359)
[    1.143888] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT4._GTF] (Node ffff93b2ce0e72f8), AE_NOT_FOUND (20160930/psparse-543)
[    1.143929] ata3.00: supports DRM functions and may not be fully accessible
[    1.143983] ata5.00: supports DRM functions and may not be fully accessible
[    1.144540] ata3.00: disabling queued TRIM support
[    1.144541] ata3.00: ATA-9: Samsung SSD 850 EVO 500GB, EMT02B6Q, max UDMA/133
[    1.144542] ata3.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.144602] ata5.00: disabling queued TRIM support
[    1.144603] ata5.00: ATA-9: Samsung SSD 850 EVO 500GB, EMT02B6Q, max UDMA/133
[    1.144604] ata5.00: 976773168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.144857] ata1.00: ATAPI: ASUS    DRW-24B5ST, 1.00, max UDMA/100
[    1.145084] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20160930/psargs-359)
[    1.145120] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT2._GTF] (Node ffff93b2ce0e71e0), AE_NOT_FOUND (20160930/psparse-543)
[    1.145178] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20160930/psargs-359)
[    1.145213] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT4._GTF] (Node ffff93b2ce0e72f8), AE_NOT_FOUND (20160930/psparse-543)
[    1.145252] ata3.00: supports DRM functions and may not be fully accessible
[    1.145276] ata5.00: supports DRM functions and may not be fully accessible

---

### Post by Doug S on 2017-05-18
Please see [this bug report]("https://bugzilla.kernel.org/show_bug.cgi?id=193531"). In particular this from my comment number 14:> So it seems, at least for me, that this issue was always there, but just not reported before. If I correctly understand bug 43229, the root issue is actually a BIOS problem.

---

