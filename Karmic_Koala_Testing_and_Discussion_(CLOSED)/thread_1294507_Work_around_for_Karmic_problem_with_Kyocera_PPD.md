---
title: "Work around for Karmic problem with Kyocera PPD"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by adair on 2009-10-18
There seems to be an incompatibility between Karmic's current printing setup (18/10/2009), and ver. 8.4 of the Kyocera PPD (certainly for the FS-C5xxxdn family).

My FS-C5100dn is no longer automatically detected on the network, as it was under Jaunty, but that is easily overcome.

The real problem follows. Under Jaunty the printer worked without issues. Under Karmic a job will produce a single sheet with a few lines of code describing the postscript setup.

The lines in the PPD concerning JCL Trapping are conflicting with something in Karmic. If you remove the following then printing will function normally (beginning line 105):

*JCLOpenUI *JCLTrapping/Trapping: PickOne
*DefaultJCLTrapping: Medium
*OrderDependency: 5 JCLSetup *JCLTrapping
*JCLTrapping Off/Off: "@PJL SET KTRAPPING=0<0A>"
*JCLTrapping Light/Light: "@PJL SET KTRAPPING=1<0A>"
*JCLTrapping Medium/Medium: "@PJL SET KTRAPPING=2<0A>"
*JCLTrapping Heavy/Heavy: "@PJL SET KTRAPPING=3<0A>"
*JCLTrapping VeryHeavy/Very heavy: "@PJL SET KTRAPPING=4<0A>"
*JCLCloseUI: *JCLTrapping

If anyone knows anything about actually solving this problem I'd welcome the news.

Best regards.

---

