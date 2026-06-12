---
title: "Comment: Edgy installation Dell 1704 FP monitor configuration error"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by jayachandranm on 2006-11-07
When I installed Edgy in my machine, it did not configure my Dell 1704 FP (Digital) flat panel monitor properly and the default screen resolution was low. The monitor was not detected as Dell monitor.

My previous installation of Dapper detected the monitor as "DELL 1704FPT" and configured with the best resolution.

I wonder why this new problem in Edgy!

To fix the issue, I manually edited the xorg.conf file of Edgy installation with the following entries:

Section "Monitor"
        Identifier      "DELL 1704FPT"
        VendorName   "Dell"
        ModelName    "Dell 1704FPT (Digital)"
        HorizSync    30.0 - 81.0
        VertRefresh  56.0 - 76.0
        Option          "DPMS"
EndSection

And added higher resolution modes under "Display" subsection.

---

