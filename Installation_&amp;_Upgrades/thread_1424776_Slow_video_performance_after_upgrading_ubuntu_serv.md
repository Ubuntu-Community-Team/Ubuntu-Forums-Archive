---
title: "Slow video performance after upgrading ubuntu server from 9.04 to 9.10"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by FranJPR on 2010-03-08
Hi,
I am running an ubuntu server with fluxbox. Since I updated to 9.10, the videos played with vlc are very slow. With 9.04, everything was fine. Any idea how to improve the performance of the graphic card again?.

Thanks

lspci | grep VGA
> 
00:01.0 VGA compatible controller: Intel Corporation 82810 (CGC) Chipset Graphics Controller (rev 03)
cat /etc/X11/xorg.conf
> 
        Identifier      "Configured Video Device"
        Option          "AccelMethod"                   "UXA"
        Option          "EXAOptimizeMigration"          "true"
        Option          "MigrationHeuristic"            "greedy"
        Option          "Tiling"                        "false" # i8xx users: see note in guide
        VideoRam        65024
EndSection

Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    16
        SubSection "Display"
                Depth   16
                Modes   "1024x768"
        EndSubSection
EndSection


---

