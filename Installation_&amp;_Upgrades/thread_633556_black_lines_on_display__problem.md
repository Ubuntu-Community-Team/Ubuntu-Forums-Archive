---
title: "black lines on display  problem"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2007-12-06
ive just installed kubuntu. on the  monitor any black is extended the width of the screen  - so i assume its a video driver problem. ive run dkpkg reconfigure xserver-xorg and tried a couple of driver options which either didi nothing or made it worse 

honor@Pooter:~$ lspci |grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV6 [Vanta/Vanta LT] (rev 15)
honor@Pooter:~$ 

 currently 

Section "Device"
  identifier "Generic Video Card"
  boardname "vesa"
  busid "PCI:1:0:0"
  driver "vesa"
  screen 0
EndSection

ection "Monitor"
  identifier "Generic Monitor"
  vendorname "AOC"
  modelname "AOC SPECTRUM 7Glr & 7GlrA"
  HorizSync 30.0-95.0
  VertRefresh 50.0-160.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  gamma 1.02
EndSection

ive tried the nv driver but that gave me a 800x640 screen resolution 
so what should I have ?

---

### Post by Pumalite on 2007-12-06
[http://ubuntuforums.org/showthread.php?t=11275](http://ubuntuforums.org/showthread.php?t=11275)

---

### Post by pdc124 on 2007-12-07
im talking a friend through doing this -  do i need to modprobe the driver fist 
honor@Pooter:~$ modprobe -l |grep nv

/lib/modules/2.6.20-16-generic/kernel/drivers/ata/sata_nv.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/video/nvidia/nvidiafb.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/char/agp/nvidia-agp.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/char/nvram.ko
/lib/modules/2.6.20-16-generic/volatile/nvidia.ko
/lib/modules/2.6.20-16-generic/volatile/nvidia_legacy.ko
/lib/modules/2.6.20-16-generic/volatile/nvidia_new.ko

honor@Pooter:~$ lsmod |grep nv 
honor@Pooter:~$

---

### Post by pdc124 on 2007-12-08
ive tried changing the driver to nvidia,nvidia_legacy adn nvidia_new and then restarting X and  X fails to start each time.

hmmmmmmmm

---

### Post by Pumalite on 2007-12-08
Post your complete specs.

---

