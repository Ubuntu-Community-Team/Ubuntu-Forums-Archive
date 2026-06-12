---
title: "Intel I865G + Dell E22WFP"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by neos2k1 on 2007-10-27
Hello 

 I have Feisty installed, my video card is Intel 865G and I have a Dell E228WFP  monitor (22" wide). 
After installing Feisty the monitor had 1024x768 resolution. I had to install the xserver-xorg-video-intel drivers. Now the native resolution is 1680x1050  which is ok.
 The problem is that after just a few minutes the X crashes. 
 Does anybody has any idea about this ? 

 Thanks.

---

### Post by neos2k1 on 2007-10-28
this is how my xorg.conf looks like. 

 Section "Device"
  identifier "Intel Corporation 82865G Integrated Graphics Controller"
  boardname "Intel 865"
  busid "PCI:0:2:0"
  driver "intel"
  screen 0
  vendorname "Intel"
EndSection

Section "Monitor"
        Identifier      "DELL E228WFP"
        Option          "DPMS"
EndSection

Section "Modes"
        Identifier      "Modes[0]"
        Modeline "1680x1050" 79.6 1152 1192 1288 1472 864 864 866 896 +hsync +vsync
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation 82865G Integrated Graphics Controller"
  Monitor "DELL E228WFP"
  DefaultDepth  24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680X1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

