---
title: "Problems with EDID post upgrade to 20.04 - mythtv system with Panasonic TV"
date: 2022-05-08
forum: Installation &amp; Upgrades
---

### Post by briggella2 on 2022-05-08
I have been running a Mythtv system v0.29 on Ubuntu 18.04 since 2018 when the system ran through a large upgrade to Myth v 31 and Ubuntu 20.04. This was a fairly traumatic process which trashed the Myth database and left the Ubuntu install semi-complete. Most of that has now been corrected but the edges of the display are off the screen all round. Initially I thought this was overscanning and tried all the usual solutions but nothing worked. I finally traced it to worng EDID data. The connection is by HDMI and has been previously working perfectly for years. The TV was bought about 2013 and is an English model. I know most people are probably onto the next version by now but the above problems are exactly why we avoid upgrading unless forced with mythtv systems.

Ubuntu is identifying the TV as a 32inch Panasonic running at 1280 x 720 whereas it is supposed to be a Panasonic LT47ET60B running at 1920 x 1080.

The EDID data is below from get-edid

> This is read-edid version 3.0.2. Prepare for some fun.Attempting to use i2c interface
Problem requesting slave address: Device or resource busy
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 4
No EDID on bus 6
No EDID on bus 8
No EDID on bus 9
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
No byte reading on this bus...
Problem requesting slave address: Bad file descriptor
12 potential busses found: 5 7 16 17 18 24 25 26 27 28 29 30
Will scan through until the first EDID is found.
Pass a bus number as an option to this program to go only for that one.
256-byte EDID successfully retrieved from i2c bus 5
If this isn't the EDID you were looking for, consider the other potential busses.
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
    Identifier "Panasonic-TV"
    ModelName "Panasonic-TV"
    VendorName "MEI"
    # Monitor Manufactured week 0 of 2013
    # EDID version 1.3
    # Digital Display
    DisplaySize 1280 720
    Gamma 2.20
    Option "DPMS" "false"
    Horizsync 15-68
    VertRefresh 23-61
    # Maximum pixel clock is 150MHz
    #Not giving standard mode: 640x480, 60Hz
    #Not giving standard mode: 800x600, 60Hz
    #Not giving standard mode: 1024x768, 60Hz
    #Not giving standard mode: 1280x1024, 60Hz


    #Extension block found. Parsing...
    Modeline     "Mode 15" 74.25 1920 2448 2492 2640 540 542 547 562 +hsync +vsync interlace
    Modeline     "Mode 0" 148.50 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 1" 148.50 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync 
    Modeline     "Mode 2" 148.500 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 3" 148.500 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 4" 74.250 1920 2448 2492 2640 1080 1082 1089 1125 +hsync +vsync interlace
    Modeline     "Mode 5" 74.250 1920 2008 2052 2200 1080 1082 1087 1125 +hsync +vsync interlace
    Modeline     "Mode 6" 74.250 1920 2558 2602 2750 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 7" 74.250 1920 2448 2492 2640 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 8" 74.250 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
    Modeline     "Mode 9" 74.250 1280 1720 1760 1980 720 725 730 750 +hsync +vsync
    Modeline     "Mode 10" 74.250 1280 1390 1420 1650 720 725 730 750 +hsync +vsync
    Modeline     "Mode 11" 27.000 720 732 796 864 576 581 586 625 -hsync -vsync
    Modeline     "Mode 12" 27.027 720 736 798 858 480 489 495 525 -hsync -vsync
    Modeline     "Mode 13" 27.000 1440 1464 1590 1728 576 578 581 625 -hsync -vsync interlace
    Modeline     "Mode 14" 27.027 1440 1478 1602 1716 480 484 487 525 -hsync -vsync interlace
    Modeline     "Mode 16" 74.25 1920 2008 2052 2200 540 542 547 562 +hsync +vsync interlace
    Modeline     "Mode 17" 85.50 1366 1436 1579 1792 768 771 774 798 +hsync +vsync 
    Option "PreferredMode" "Mode 15"
EndSection





I am currently running it at 1366 x 768

Any ideas how to get Ubuntu to identify the TV correctly so the resolution in display matches the hardware detected correctly.

Thanks in advance.

---

