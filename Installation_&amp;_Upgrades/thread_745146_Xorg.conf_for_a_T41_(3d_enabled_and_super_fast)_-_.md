---
title: "Xorg.conf for a T41 (3d enabled and super fast) - 7500 Mobility"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by vdings on 2008-04-04
I struggled to get the kind of performance i saw under XP.

I have finally got it.

here is the device section of the xorg.conf

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "ATI Radeon"
        Busid           "PCI:1:0:0"
        Driver          "radeon"
        Screen  0
        Vendorname      "ATI"
        Option          "MergedFB"      "off"
        Option          "AccelMethod" "EXA"
        Option          "EXANoComposite" "false"
#       Option          "AGPFastWrite" "On"
        Option          "FBTexPercent" "50"
        Option          "MigrationHeuristic" "greedy"
        Option          "DRI" "true"
        Option          "GARTSize"      "256"
        Option          "AGPMode" "4"
        Option          "Colortiling" "On"
EndSection

---

