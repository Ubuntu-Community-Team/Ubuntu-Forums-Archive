---
title: "touch not working after fresh install 18.04.1 LTS aarch64, were working in 16.04"
date: 2018-11-27
forum: Installation &amp; Upgrades
---

### Post by sboyce on 2018-11-27
I have 2 touch screens not working and one that works.
Bus 001 Device 010: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen on 2 ODROID-C2's, touch not working. I also tried xinput_calibrator.
root@hiqsdr64:~# cat /usr/share/X11/xorg.conf.d/99-calibration.conf 
Section "InputClass"
        Identifier      "calibration"
        MatchProduct    "eGalax Inc. USB TouchController"
        Option  "MinX"  "-137"
        Option  "MaxX"  "65508"
        Option  "MinY"  "637"
        Option  "MaxY"  "64898"
        Option  "SwapXY"        "0" # unless it was already set to 1
        Option  "InvertX"       "0"  # unless it was already set
        Option  "InvertY"       "0"  # unless it was already set
EndSection

Bus 001 Device 004: ID 0eef:0005 D-WAV Scientific Co., Ltd on one ODROID-C2 works out of the box with no /usr/share/X11/xorg.conf.d/99-calibration.conf.

---

