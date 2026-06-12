---
title: "ubuntu setup on hdmi plasma connection"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by hithere27 on 2007-11-05
im trying to install ubuntu 7.10 on a Gigabyte Mainboard with HDMI. Its connected to my Plasma from Panasonic 42" full HD.
when i boot the pc it switched to vga mode and i get the normal boot screen via hdmi port. even setup menue works good, but when i choose install it turns black and stays dark. only thing possible to get picture is to re-attach vga cable and turn to other channel.

any way to solve this or get text install running ?

---

### Post by powertower on 2007-11-05
First things first, I'm a Ubuntu noob! When you start the installation for Ubuntu, it installs semi-generic video card drivers will all defaults configured. Your best bet is to get Ubuntu installation finished on the 15pin vga cable and install/configure your video outputs afterwards. I'm sure there is a way to get HDMI support through a few terminal commands but it would be simpler to do the above statement. If someone wants to respond to your thread, include more specifics about your hardware, what kind of gigabyte motherboard and what video card?

The reason why the BIOS boot screen and install screen works is because your bios is controlling the video outputs, but later when you click install, Ubuntu installation takes over. GOOD LUCK

-POWERTOWER-

---

### Post by hithere27 on 2007-11-05
hi there,
thx for the answer

hardware is Intel Core2Duo on Gigabyte GA-G33M-S2H Mainboard with Onboard Video Intel GMA3100

i have it installed now, like you said via VGA cable. but still cant get my plasma to work on the hdmi port (to show desktop).
all vga pics work (when its booting or so) on both screens but as soon as it switches to a higher mode vga stays and hdmi turns black.

its showing 2 graphic cards in "screen and graphics", 1st one using intel driver, 2nd one using vesa.
i cant seem to switch ON a 2nd monitor in "screen resolution" either.

ill post my xorg.conf and the log in the next reply

Section "Device"
        Identifier      "Intel Corporation Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "PANASONIC-TV"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Integrated Graphics Controller"
        Monitor         "PANASONIC-TV"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1920x540"
        EndSubSection
EndSection

---

### Post by hithere27 on 2007-11-05
here is the log

(II) intel(0): Output VGA using monitor section PANASONIC-TV
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): SDVO device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): Output VGA connected
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): EDID for output VGA
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)

(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TMDS-1 connected
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID for output TMDS-1
(II) intel(0): Manufacturer: MEI  Model: a064  Serial#: 1649
(II) intel(0): Year: 2007  Week: 35
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.345   greenX: 0.291 greenY: 0.635
(II) intel(0): blueX: 0.163 blueY: 0.093   whiteX: 0.288 whiteY: 0.296
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 74.2 MHz   Image Size:  1434 x 806 mm
(II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 74.2 MHz   Image Size:  1434 x 806 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) intel(0): Monitor name: PANASONIC-TV
(II) intel(0): Ranges: V min: 23  V max: 61 Hz, H min: 15  H max: 68 kHz, PixClock max 150 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0034a964a071060000
(II) intel(0):  23110103800000780adaffa3584aa229
(II) intel(0):  17494b00000001010101010101010101
(II) intel(0):  010101010101011d80d0721c1620102c
(II) intel(0):  25809a265300009e011d8018711c1620
(II) intel(0):  582c25009a265300009e000000fc0050
(II) intel(0):  414e41534f4e49432d54560a000000fd
(II) intel(0):  00173d0f440f000a2020202020200142
(II) intel(0): EDID vendor "MEI", prod id 41060
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Printing probed modes for output TMDS-1
(II) intel(0): Modeline "1920x540"x100.1   74.25  1920 2448 2492 2640  540 542 547 562 interlace +hsync +vsync (28.1 kHz)
(II) intel(0): Modeline "1920x540"x120.1   74.25  1920 2008 2052 2200  540 542 547 562 interlace +hsync +vsync (33.8 kHz)
(II) intel(0): Output VGA connected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output VGA using initial mode 1280x768
(II) intel(0): Output TMDS-1 using initial mode 1920x540
(II) intel(0): detected 1024 kB GTT.
(II) intel(0): detected 7164 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"


(II) intel(0): Printing probed modes for output VGA
(II) intel(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) intel(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output TMDS-1 connected
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID for output TMDS-1
(II) intel(0): Manufacturer: MEI  Model: a064  Serial#: 1649
(II) intel(0): Year: 2007  Week: 35
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: H-Size may change,  V-Size may change
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.640 redY: 0.345   greenX: 0.291 greenY: 0.635
(II) intel(0): blueX: 0.163 blueY: 0.093   whiteX: 0.288 whiteY: 0.296
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 74.2 MHz   Image Size:  1434 x 806 mm
(II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 74.2 MHz   Image Size:  1434 x 806 mm
(II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) intel(0): Monitor name: PANASONIC-TV
(II) intel(0): Ranges: V min: 23  V max: 61 Hz, H min: 15  H max: 68 kHz, PixClock max 150 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0):  00ffffffffffff0034a964a071060000
(II) intel(0):  23110103800000780adaffa3584aa229
(II) intel(0):  17494b00000001010101010101010101
(II) intel(0):  010101010101011d80d0721c1620102c
(II) intel(0):  25809a265300009e011d8018711c1620
(II) intel(0):  582c25009a265300009e000000fc0050
(II) intel(0):  414e41534f4e49432d54560a000000fd
(II) intel(0):  00173d0f440f000a2020202020200142
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1920x540"   74.25  1920 2448 2492 2640  540 542 547 562 interlace +hsync +vsync
(II) intel(0): Modeline "1920x540"   74.25  1920 2008 2052 2200  540 542 547 562 interlace +hsync +vsync
(II) intel(0): EDID vendor "MEI", prod id 41060
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)

---

### Post by hithere27 on 2007-11-06
anyone have a clue ?

---

### Post by paahtis75 on 2008-01-03
Having same problems to connection GA-G33M-S2H to Sony KDF50E2010 via HDMI-HDMI or DVI-HDMI using onboard GMA3100. Tv and cable are ok because same system works with GF7600 almost out-of-the box:

Used xorg.conf with onboard card:
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
   Identifier   "Generic Keyboard"
   Driver      "kbd"
   Option      "CoreKeyboard"
   Option      "XkbRules"   "xorg"
   Option      "XkbModel"   "pc105"
   Option      "XkbLayout"   "fi"
EndSection

Section "InputDevice"
   Identifier   "Configured Mouse"
   Driver      "mouse"
   Option      "CorePointer"
   Option      "Device"      "/dev/input/mice"
   Option      "Protocol"      "ImPS/2"
   Option      "ZAxisMapping"      "4 5"
   Option      "Emulate3Buttons"   "true"
EndSection

Section "InputDevice"
   Driver      "wacom"
   Identifier   "stylus"
   Option      "Device"   "/dev/input/wacom"
   Option      "Type"      "stylus"
   Option      "ForceDevice"   "ISDV4"      # Tablet PC ONLY
EndSection

Section "InputDevice"
   Driver      "wacom"
   Identifier   "eraser"
   Option      "Device"   "/dev/input/wacom"
   Option      "Type"      "eraser"
   Option      "ForceDevice"   "ISDV4"      # Tablet PC ONLY
EndSection

Section "InputDevice"
   Driver      "wacom"
   Identifier   "cursor"
   Option      "Device"   "/dev/input/wacom"
   Option      "Type"      "cursor"
   Option      "ForceDevice"   "ISDV4"      # Tablet PC ONLY
EndSection

Section "Device"
   Identifier   "Intel Corporation Integrated Graphics Controller"
   Driver      "intel"
   BusID      "PCI:0:2:0"
EndSection

Section "Monitor"
   Identifier   "SONY TV"
   Option      "DPMS"
  # 1280x720 @ 50.00 Hz (GTF) hsync: 37.05 kHz; pclk: 60.47 MHz
  Modeline "1280x720_50.00"  60.47  1280 1328 1456 1632  720 721 724 741  -HSync +Vsync
 # 1280x720 @ 60.00 Hz (GTF) hsync: 44.76 kHz; pclk: 74.48 MHz
  Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync

EndSection

Section "Screen"
   Identifier   "Default Screen"
   Device      "Intel Corporation Integrated Graphics Controller"
   Monitor      "SONY TV"
   DefaultDepth   24
   SubSection "Display"
      Modes      "1280x720_60.00" "1280x720_50.00" "1920x540" "720x480"
   EndSubSection
EndSection

Section "ServerLayout"
   Identifier   "Default Layout"
   Screen      "Default Screen"
   InputDevice   "Generic Keyboard"
   InputDevice   "Configured Mouse"

# Uncomment if you have a wacom tablet
#   InputDevice     "stylus"   "SendCoreEvents"
#   InputDevice     "cursor"   "SendCoreEvents"
#   InputDevice     "eraser"   "SendCoreEvents"
EndSection

```


Xorg.0.log

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux nokkalisko 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
   Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
   to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
   (++) from command line, (!!) notice, (II) informational,
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 28 20:14:31 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SONY TV"
(**) |   |-->Device "Intel Corporation Integrated Graphics Controller"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
   Entry deleted from font path.
(==) FontPath set to:
   /usr/share/fonts/X11/misc,
   /usr/share/fonts/X11/100dpi/:unscaled,
   /usr/share/fonts/X11/75dpi/:unscaled,
   /usr/share/fonts/X11/Type1,
   /usr/share/fonts/X11/100dpi,
   /usr/share/fonts/X11/75dpi,
   /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
   X.Org ANSI C Emulation: 0.3
   X.Org Video Driver: 1.2
   X.Org XInput driver : 0.7
   X.Org Server Extension : 0.3
   X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.0.0
   ABI class: X.Org Video Driver, version 1.2
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29c0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,29c2 card 1458,d000 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,29c3 card 1458,d000 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2937 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1458,a022 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2918 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2921 card 1458,b002 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2926 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 02:00:0: chip 197b,2368 card 1458,b000 rev 00 class 01,01,85 hdr 00
(II) PCI: 03:00:0: chip 1131,7146 card 153b,1176 rev 01 class 04,80,00 hdr 00
(II) PCI: 03:01:0: chip 1131,7146 card 153b,1176 rev 01 class 04,80,00 hdr 00
(II) PCI: 03:05:0: chip 10ec,8167 card 1458,e000 rev 10 class 02,00,00 hdr 00
(II) PCI: 03:07:0: chip 104c,8024 card 1458,1000 rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
   [0] -1   0   0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:28:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 1 I/O range:
   [0] -1   0   0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:4), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
   [0] -1   0   0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
   [0] -1   0   0xf0000000 - 0xf0ffffff (0x1000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
   [0] -1   0   0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
   [0] -1   0   0xf1000000 - 0xf2ffffff (0x2000000) MX[B]
(II) Bus 3 prefetchable memory range:
   [0] -1   0   0x80000000 - 0x800fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Integrated Graphics Controller rev 2, Mem @ 0xf3100000/19, 0xe0000000/28, 0xf3000000/20, I/O @ 0xd200/3
(--) PCI: (0:2:1) Intel Corporation Integrated Graphics Controller rev 2, Mem @ 0xf3180000/19
(II) Addressable bus resource ranges are
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B]
   [1] -1   0   0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [5] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
   [0] -1   0   0xf2000000 - 0xf2003fff (0x4000) MX[B]
   [1] -1   0   0xf2006000 - 0xf20067ff (0x800) MX[B]
   [2] -1   0   0xf2004000 - 0xf20040ff (0x100) MX[B]
   [3] -1   0   0xf2007000 - 0xf20071ff (0x200) MX[B]
   [4] -1   0   0xf2005000 - 0xf20051ff (0x200) MX[B]
   [5] -1   0   0xf3206000 - 0xf32060ff (0x100) MX[B]
   [6] -1   0   0xf3204000 - 0xf32043ff (0x400) MX[B]
   [7] -1   0   0xf3200000 - 0xf3203fff (0x4000) MX[B]
   [8] -1   0   0xf3205000 - 0xf32053ff (0x400) MX[B]
   [9] -1   0   0xf3180000 - 0xf31fffff (0x80000) MX[B](B)
   [10] -1   0   0xf3000000 - 0xf30fffff (0x100000) MX[B](B)
   [11] -1   0   0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
   [12] -1   0   0xf3100000 - 0xf317ffff (0x80000) MX[B](B)
   [13] -1   0   0x0000c000 - 0x0000c0ff (0x100) IX[B]
   [14] -1   0   0x0000b400 - 0x0000b40f (0x10) IX[B]
   [15] -1   0   0x0000b300 - 0x0000b303 (0x4) IX[B]
   [16] -1   0   0x0000b200 - 0x0000b207 (0x8) IX[B]
   [17] -1   0   0x0000b100 - 0x0000b103 (0x4) IX[B]
   [18] -1   0   0x0000b000 - 0x0000b007 (0x8) IX[B]
   [19] -1   0   0x0000e300 - 0x0000e30f (0x10) IX[B]
   [20] -1   0   0x0000e200 - 0x0000e20f (0x10) IX[B]
   [21] -1   0   0x0000e100 - 0x0000e103 (0x4) IX[B]
   [22] -1   0   0x0000e000 - 0x0000e007 (0x8) IX[B]
   [23] -1   0   0x0000df00 - 0x0000df03 (0x4) IX[B]
   [24] -1   0   0x0000de00 - 0x0000de07 (0x8) IX[B]
   [25] -1   0   0x00000500 - 0x0000051f (0x20) IX[B]
   [26] -1   0   0x0000dc00 - 0x0000dc0f (0x10) IX[B]
   [27] -1   0   0x0000db00 - 0x0000db0f (0x10) IX[B]
   [28] -1   0   0x0000da00 - 0x0000da03 (0x4) IX[B]
   [29] -1   0   0x0000d900 - 0x0000d907 (0x8) IX[B]
   [30] -1   0   0x0000d800 - 0x0000d803 (0x4) IX[B]
   [31] -1   0   0x0000d700 - 0x0000d707 (0x8) IX[B]
   [32] -1   0   0x0000d500 - 0x0000d51f (0x20) IX[B]
   [33] -1   0   0x0000d400 - 0x0000d41f (0x20) IX[B]
   [34] -1   0   0x0000d300 - 0x0000d31f (0x20) IX[B]
   [35] -1   0   0x0000d100 - 0x0000d11f (0x20) IX[B]
   [36] -1   0   0x0000d000 - 0x0000d01f (0x20) IX[B]
   [37] -1   0   0x0000d600 - 0x0000d61f (0x20) IX[B]
   [38] -1   0   0x0000d200 - 0x0000d207 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
   [0] -1   0   0xf2000000 - 0xf2003fff (0x4000) MX[B]
   [1] -1   0   0xf2006000 - 0xf20067ff (0x800) MX[B]
   [2] -1   0   0xf2004000 - 0xf20040ff (0x100) MX[B]
   [3] -1   0   0xf2007000 - 0xf20071ff (0x200) MX[B]
   [4] -1   0   0xf2005000 - 0xf20051ff (0x200) MX[B]
   [5] -1   0   0xf3206000 - 0xf32060ff (0x100) MX[B]
   [6] -1   0   0xf3204000 - 0xf32043ff (0x400) MX[B]
   [7] -1   0   0xf3200000 - 0xf3203fff (0x4000) MX[B]
   [8] -1   0   0xf3205000 - 0xf32053ff (0x400) MX[B]
   [9] -1   0   0xf3180000 - 0xf31fffff (0x80000) MX[B](B)
   [10] -1   0   0xf3000000 - 0xf30fffff (0x100000) MX[B](B)
   [11] -1   0   0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
   [12] -1   0   0xf3100000 - 0xf317ffff (0x80000) MX[B](B)
   [13] -1   0   0x0000c000 - 0x0000c0ff (0x100) IX[B]
   [14] -1   0   0x0000b400 - 0x0000b40f (0x10) IX[B]
   [15] -1   0   0x0000b300 - 0x0000b303 (0x4) IX[B]
   [16] -1   0   0x0000b200 - 0x0000b207 (0x8) IX[B]
   [17] -1   0   0x0000b100 - 0x0000b103 (0x4) IX[B]
   [18] -1   0   0x0000b000 - 0x0000b007 (0x8) IX[B]
   [19] -1   0   0x0000e300 - 0x0000e30f (0x10) IX[B]
   [20] -1   0   0x0000e200 - 0x0000e20f (0x10) IX[B]
   [21] -1   0   0x0000e100 - 0x0000e103 (0x4) IX[B]
   [22] -1   0   0x0000e000 - 0x0000e007 (0x8) IX[B]
   [23] -1   0   0x0000df00 - 0x0000df03 (0x4) IX[B]
   [24] -1   0   0x0000de00 - 0x0000de07 (0x8) IX[B]
   [25] -1   0   0x00000500 - 0x0000051f (0x20) IX[B]
   [26] -1   0   0x0000dc00 - 0x0000dc0f (0x10) IX[B]
   [27] -1   0   0x0000db00 - 0x0000db0f (0x10) IX[B]
   [28] -1   0   0x0000da00 - 0x0000da03 (0x4) IX[B]
   [29] -1   0   0x0000d900 - 0x0000d907 (0x8) IX[B]
   [30] -1   0   0x0000d800 - 0x0000d803 (0x4) IX[B]
   [31] -1   0   0x0000d700 - 0x0000d707 (0x8) IX[B]
   [32] -1   0   0x0000d500 - 0x0000d51f (0x20) IX[B]
   [33] -1   0   0x0000d400 - 0x0000d41f (0x20) IX[B]
   [34] -1   0   0x0000d300 - 0x0000d31f (0x20) IX[B]
   [35] -1   0   0x0000d100 - 0x0000d11f (0x20) IX[B]
   [36] -1   0   0x0000d000 - 0x0000d01f (0x20) IX[B]
   [37] -1   0   0x0000d600 - 0x0000d61f (0x20) IX[B]
   [38] -1   0   0x0000d200 - 0x0000d207 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [5] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0xf2000000 - 0xf2003fff (0x4000) MX[B]
   [5] -1   0   0xf2006000 - 0xf20067ff (0x800) MX[B]
   [6] -1   0   0xf2004000 - 0xf20040ff (0x100) MX[B]
   [7] -1   0   0xf2007000 - 0xf20071ff (0x200) MX[B]
   [8] -1   0   0xf2005000 - 0xf20051ff (0x200) MX[B]
   [9] -1   0   0xf3206000 - 0xf32060ff (0x100) MX[B]
   [10] -1   0   0xf3204000 - 0xf32043ff (0x400) MX[B]
   [11] -1   0   0xf3200000 - 0xf3203fff (0x4000) MX[B]
   [12] -1   0   0xf3205000 - 0xf32053ff (0x400) MX[B]
   [13] -1   0   0xf3180000 - 0xf31fffff (0x80000) MX[B](B)
   [14] -1   0   0xf3000000 - 0xf30fffff (0x100000) MX[B](B)
   [15] -1   0   0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
   [16] -1   0   0xf3100000 - 0xf317ffff (0x80000) MX[B](B)
   [17] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [18] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [19] -1   0   0x0000c000 - 0x0000c0ff (0x100) IX[B]
   [20] -1   0   0x0000b400 - 0x0000b40f (0x10) IX[B]
   [21] -1   0   0x0000b300 - 0x0000b303 (0x4) IX[B]
   [22] -1   0   0x0000b200 - 0x0000b207 (0x8) IX[B]
   [23] -1   0   0x0000b100 - 0x0000b103 (0x4) IX[B]
   [24] -1   0   0x0000b000 - 0x0000b007 (0x8) IX[B]
   [25] -1   0   0x0000e300 - 0x0000e30f (0x10) IX[B]
   [26] -1   0   0x0000e200 - 0x0000e20f (0x10) IX[B]
   [27] -1   0   0x0000e100 - 0x0000e103 (0x4) IX[B]
   [28] -1   0   0x0000e000 - 0x0000e007 (0x8) IX[B]
   [29] -1   0   0x0000df00 - 0x0000df03 (0x4) IX[B]
   [30] -1   0   0x0000de00 - 0x0000de07 (0x8) IX[B]
   [31] -1   0   0x00000500 - 0x0000051f (0x20) IX[B]
   [32] -1   0   0x0000dc00 - 0x0000dc0f (0x10) IX[B]
   [33] -1   0   0x0000db00 - 0x0000db0f (0x10) IX[B]
   [34] -1   0   0x0000da00 - 0x0000da03 (0x4) IX[B]
   [35] -1   0   0x0000d900 - 0x0000d907 (0x8) IX[B]
   [36] -1   0   0x0000d800 - 0x0000d803 (0x4) IX[B]
   [37] -1   0   0x0000d700 - 0x0000d707 (0x8) IX[B]
   [38] -1   0   0x0000d500 - 0x0000d51f (0x20) IX[B]
   [39] -1   0   0x0000d400 - 0x0000d41f (0x20) IX[B]
   [40] -1   0   0x0000d300 - 0x0000d31f (0x20) IX[B]
   [41] -1   0   0x0000d100 - 0x0000d11f (0x20) IX[B]
   [42] -1   0   0x0000d000 - 0x0000d01f (0x20) IX[B]
   [43] -1   0   0x0000d600 - 0x0000d61f (0x20) IX[B]
   [44] -1   0   0x0000d200 - 0x0000d207 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.0.0
   Module class: X.Org Server Extension
   ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.0.0
   Module class: X.Org Server Extension
   ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.0.0
   ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
   compiled for 1.3.0, module version = 2.1.0
   Module class: X.Org Font Renderer
   ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.13.0
   Module class: X.Org Server Extension
   ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.0.0
   ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 2.1.1
   Module class: X.Org Video Driver
   ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.2.1
   Module class: X.Org XInput Driver
   ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.2.1
   Module class: X.Org XInput Driver
   ABI class: X.Org XInput driver, version 0.7
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
   i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
   E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
   965GM, 965GME/GLE, G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset G33 found
(II) resource ranges after xf86ClaimFixedResources() call:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0xf2000000 - 0xf2003fff (0x4000) MX[B]
   [5] -1   0   0xf2006000 - 0xf20067ff (0x800) MX[B]
   [6] -1   0   0xf2004000 - 0xf20040ff (0x100) MX[B]
   [7] -1   0   0xf2007000 - 0xf20071ff (0x200) MX[B]
   [8] -1   0   0xf2005000 - 0xf20051ff (0x200) MX[B]
   [9] -1   0   0xf3206000 - 0xf32060ff (0x100) MX[B]
   [10] -1   0   0xf3204000 - 0xf32043ff (0x400) MX[B]
   [11] -1   0   0xf3200000 - 0xf3203fff (0x4000) MX[B]
   [12] -1   0   0xf3205000 - 0xf32053ff (0x400) MX[B]
   [13] -1   0   0xf3180000 - 0xf31fffff (0x80000) MX[B](B)
   [14] -1   0   0xf3000000 - 0xf30fffff (0x100000) MX[B](B)
   [15] -1   0   0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
   [16] -1   0   0xf3100000 - 0xf317ffff (0x80000) MX[B](B)
   [17] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [18] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [19] -1   0   0x0000c000 - 0x0000c0ff (0x100) IX[B]
   [20] -1   0   0x0000b400 - 0x0000b40f (0x10) IX[B]
   [21] -1   0   0x0000b300 - 0x0000b303 (0x4) IX[B]
   [22] -1   0   0x0000b200 - 0x0000b207 (0x8) IX[B]
   [23] -1   0   0x0000b100 - 0x0000b103 (0x4) IX[B]
   [24] -1   0   0x0000b000 - 0x0000b007 (0x8) IX[B]
   [25] -1   0   0x0000e300 - 0x0000e30f (0x10) IX[B]
   [26] -1   0   0x0000e200 - 0x0000e20f (0x10) IX[B]
   [27] -1   0   0x0000e100 - 0x0000e103 (0x4) IX[B]
   [28] -1   0   0x0000e000 - 0x0000e007 (0x8) IX[B]
   [29] -1   0   0x0000df00 - 0x0000df03 (0x4) IX[B]
   [30] -1   0   0x0000de00 - 0x0000de07 (0x8) IX[B]
   [31] -1   0   0x00000500 - 0x0000051f (0x20) IX[B]
   [32] -1   0   0x0000dc00 - 0x0000dc0f (0x10) IX[B]
   [33] -1   0   0x0000db00 - 0x0000db0f (0x10) IX[B]
   [34] -1   0   0x0000da00 - 0x0000da03 (0x4) IX[B]
   [35] -1   0   0x0000d900 - 0x0000d907 (0x8) IX[B]
   [36] -1   0   0x0000d800 - 0x0000d803 (0x4) IX[B]
   [37] -1   0   0x0000d700 - 0x0000d707 (0x8) IX[B]
   [38] -1   0   0x0000d500 - 0x0000d51f (0x20) IX[B]
   [39] -1   0   0x0000d400 - 0x0000d41f (0x20) IX[B]
   [40] -1   0   0x0000d300 - 0x0000d31f (0x20) IX[B]
   [41] -1   0   0x0000d100 - 0x0000d11f (0x20) IX[B]
   [42] -1   0   0x0000d000 - 0x0000d01f (0x20) IX[B]
   [43] -1   0   0x0000d600 - 0x0000d61f (0x20) IX[B]
   [44] -1   0   0x0000d200 - 0x0000d207 (0x8) IX[B](B)
(II) resource ranges after probing:
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [4] -1   0   0xf2000000 - 0xf2003fff (0x4000) MX[B]
   [5] -1   0   0xf2006000 - 0xf20067ff (0x800) MX[B]
   [6] -1   0   0xf2004000 - 0xf20040ff (0x100) MX[B]
   [7] -1   0   0xf2007000 - 0xf20071ff (0x200) MX[B]
   [8] -1   0   0xf2005000 - 0xf20051ff (0x200) MX[B]
   [9] -1   0   0xf3206000 - 0xf32060ff (0x100) MX[B]
   [10] -1   0   0xf3204000 - 0xf32043ff (0x400) MX[B]
   [11] -1   0   0xf3200000 - 0xf3203fff (0x4000) MX[B]
   [12] -1   0   0xf3205000 - 0xf32053ff (0x400) MX[B]
   [13] -1   0   0xf3180000 - 0xf31fffff (0x80000) MX[B](B)
   [14] -1   0   0xf3000000 - 0xf30fffff (0x100000) MX[B](B)
   [15] -1   0   0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
   [16] -1   0   0xf3100000 - 0xf317ffff (0x80000) MX[B](B)
   [17] 0   0   0x000a0000 - 0x000affff (0x10000) MS[B]
   [18] 0   0   0x000b0000 - 0x000b7fff (0x8000) MS[B]
   [19] 0   0   0x000b8000 - 0x000bffff (0x8000) MS[B]
   [20] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [21] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [22] -1   0   0x0000c000 - 0x0000c0ff (0x100) IX[B]
   [23] -1   0   0x0000b400 - 0x0000b40f (0x10) IX[B]
   [24] -1   0   0x0000b300 - 0x0000b303 (0x4) IX[B]
   [25] -1   0   0x0000b200 - 0x0000b207 (0x8) IX[B]
   [26] -1   0   0x0000b100 - 0x0000b103 (0x4) IX[B]
   [27] -1   0   0x0000b000 - 0x0000b007 (0x8) IX[B]
   [28] -1   0   0x0000e300 - 0x0000e30f (0x10) IX[B]
   [29] -1   0   0x0000e200 - 0x0000e20f (0x10) IX[B]
   [30] -1   0   0x0000e100 - 0x0000e103 (0x4) IX[B]
   [31] -1   0   0x0000e000 - 0x0000e007 (0x8) IX[B]
   [32] -1   0   0x0000df00 - 0x0000df03 (0x4) IX[B]
   [33] -1   0   0x0000de00 - 0x0000de07 (0x8) IX[B]
   [34] -1   0   0x00000500 - 0x0000051f (0x20) IX[B]
   [35] -1   0   0x0000dc00 - 0x0000dc0f (0x10) IX[B]
   [36] -1   0   0x0000db00 - 0x0000db0f (0x10) IX[B]
   [37] -1   0   0x0000da00 - 0x0000da03 (0x4) IX[B]
   [38] -1   0   0x0000d900 - 0x0000d907 (0x8) IX[B]
   [39] -1   0   0x0000d800 - 0x0000d803 (0x4) IX[B]
   [40] -1   0   0x0000d700 - 0x0000d707 (0x8) IX[B]
   [41] -1   0   0x0000d500 - 0x0000d51f (0x20) IX[B]
   [42] -1   0   0x0000d400 - 0x0000d41f (0x20) IX[B]
   [43] -1   0   0x0000d300 - 0x0000d31f (0x20) IX[B]
   [44] -1   0   0x0000d100 - 0x0000d11f (0x20) IX[B]
   [45] -1   0   0x0000d000 - 0x0000d01f (0x20) IX[B]
   [46] -1   0   0x0000d600 - 0x0000d61f (0x20) IX[B]
   [47] -1   0   0x0000d200 - 0x0000d207 (0x8) IX[B](B)
   [48] 0   0   0x000003b0 - 0x000003bb (0xc) IS[B]
   [49] 0   0   0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.0.0
   ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.1.0
   ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 0.1.0
   ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G33
(--) intel(0): Chipset: "G33"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xF3100000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
   for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section SONY TV
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): SDVO device VID/DID: 04:AE.00, clock range 25.0MHz - 165.0MHz, input 1: Y, input 2: N, output 1: Y, output 2: N
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output TMDS-1 connected
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" removed.
(II) intel(0): EDID for output TMDS-1
(II) intel(0): Manufacturer: SNY  Model: 9600  Serial#: 16843009
(II) intel(0): Year: 2005  Week: 50
(II) intel(0): EDID Version: 1.3
(II) intel(0): Digital Display Input
(II) intel(0): Max H-Image Size [cm]: horiz.: 70  vert.: 40
(II) intel(0): Gamma: 2.20
(II) intel(0): No DPMS capabilities specified; RGB/Color Display
(II) intel(0): First detailed timing is preferred mode
(II) intel(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) intel(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 74.2 MHz   Image Size:  735 x 420 mm
(II) intel(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
(II) intel(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
(II) intel(0): Supported additional Video Mode:
(II) intel(0): clock: 27.0 MHz   Image Size:  735 x 420 mm
(II) intel(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
(II) intel(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
(II) intel(0): Monitor name: SONY TV
(II) intel(0): Ranges: V min: 48  V max: 62 Hz, H min: 14  H max: 46 kHz, PixClock max 80 MHz
(II) intel(0): Number of EDID sections to follow: 1
(II) intel(0): EDID (in hex):
(II) intel(0):    00ffffffffffff004dd9009601010101
(II) intel(0):    320f0103804628780a0dc9a057479827
(II) intel(0):    12484c00000001010101010101010101
(II) intel(0):    010101010101011d80d0721c1620102c
(II) intel(0):    2580dfa42100009e8c0ad08a20e02d10
(II) intel(0):    103e9600dfa421000018000000fc0053
(II) intel(0):    4f4e592054560a2020202020000000fd
(II) intel(0):    00303e0e2e08000a20202020202001b3
(II) intel(0): EDID vendor "SNY", prod id 38400
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Printing probed modes for output TMDS-1
(II) intel(0): Modeline "1920x540"x100.1   74.25  1920 2448 2492 2640  540 542 547 562 interlace +hsync +vsync (28.1 kHz)
(II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 connected
(II) intel(0): Output TMDS-1 using initial mode 1920x540
(II) intel(0): detected 1024 kB GTT.
(II) intel(0): detected 7164 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(++) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.0.0
   ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
   compiled for 1.3.0, module version = 1.2.0
   ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
   [0] 0   0   0xf3000000 - 0xf30fffff (0x100000) MS[B]
   [1] 0   0   0xe0000000 - 0xefffffff (0x10000000) MS[B]
   [2] 0   0   0xf3100000 - 0xf317ffff (0x80000) MS[B]
   [3] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
   [4] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B]
   [5] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B]
   [6] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B]
   [7] -1   0   0xf2000000 - 0xf2003fff (0x4000) MX[B]
   [8] -1   0   0xf2006000 - 0xf20067ff (0x800) MX[B]
   [9] -1   0   0xf2004000 - 0xf20040ff (0x100) MX[B]
   [10] -1   0   0xf2007000 - 0xf20071ff (0x200) MX[B]
   [11] -1   0   0xf2005000 - 0xf20051ff (0x200) MX[B]
   [12] -1   0   0xf3206000 - 0xf32060ff (0x100) MX[B]
   [13] -1   0   0xf3204000 - 0xf32043ff (0x400) MX[B]
   [14] -1   0   0xf3200000 - 0xf3203fff (0x4000) MX[B]
   [15] -1   0   0xf3205000 - 0xf32053ff (0x400) MX[B]
   [16] -1   0   0xf3180000 - 0xf31fffff (0x80000) MX[B](B)
   [17] -1   0   0xf3000000 - 0xf30fffff (0x100000) MX[B](B)
   [18] -1   0   0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
   [19] -1   0   0xf3100000 - 0xf317ffff (0x80000) MX[B](B)
   [20] 0   0   0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
   [21] 0   0   0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
   [22] 0   0   0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
   [23] 0   0   0x0000d200 - 0x0000d207 (0x8) IS[B]
   [24] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B]
   [25] -1   0   0x00000000 - 0x000000ff (0x100) IX[B]
   [26] -1   0   0x0000c000 - 0x0000c0ff (0x100) IX[B]
   [27] -1   0   0x0000b400 - 0x0000b40f (0x10) IX[B]
   [28] -1   0   0x0000b300 - 0x0000b303 (0x4) IX[B]
   [29] -1   0   0x0000b200 - 0x0000b207 (0x8) IX[B]
   [30] -1   0   0x0000b100 - 0x0000b103 (0x4) IX[B]
   [31] -1   0   0x0000b000 - 0x0000b007 (0x8) IX[B]
   [32] -1   0   0x0000e300 - 0x0000e30f (0x10) IX[B]
   [33] -1   0   0x0000e200 - 0x0000e20f (0x10) IX[B]
   [34] -1   0   0x0000e100 - 0x0000e103 (0x4) IX[B]
   [35] -1   0   0x0000e000 - 0x0000e007 (0x8) IX[B]
   [36] -1   0   0x0000df00 - 0x0000df03 (0x4) IX[B]
   [37] -1   0   0x0000de00 - 0x0000de07 (0x8) IX[B]
   [38] -1   0   0x00000500 - 0x0000051f (0x20) IX[B]
   [39] -1   0   0x0000dc00 - 0x0000dc0f (0x10) IX[B]
   [40] -1   0   0x0000db00 - 0x0000db0f (0x10) IX[B]
   [41] -1   0   0x0000da00 - 0x0000da03 (0x4) IX[B]
   [42] -1   0   0x0000d900 - 0x0000d907 (0x8) IX[B]
   [43] -1   0   0x0000d800 - 0x0000d803 (0x4) IX[B]
   [44] -1   0   0x0000d700 - 0x0000d707 (0x8) IX[B]
   [45] -1   0   0x0000d500 - 0x0000d51f (0x20) IX[B]
   [46] -1   0   0x0000d400 - 0x0000d41f (0x20) IX[B]
   [47] -1   0   0x0000d300 - 0x0000d31f (0x20) IX[B]
   [48] -1   0   0x0000d100 - 0x0000d11f (0x20) IX[B]
   [49] -1   0   0x0000d000 - 0x0000d01f (0x20) IX[B]
   [50] -1   0   0x0000d600 - 0x0000d61f (0x20) IX[B]
   [51] -1   0   0x0000d200 - 0x0000d207 (0x8) IX[B](B)
   [52] 0   0   0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
   [53] 0   0   0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 488704 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1954812 kB available
(==) intel(0): VideoRam: 262144 KB
(II) intel(0): Attempting memory allocation with tiled buffers and
          large DRI memory manager reservation:
(II) intel(0): Allocating 6780 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1920 -> 2048).
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB)
(II) intel(0): 0x00033000-0x00033fff: G33 hw status (4 kB)
(II) intel(0): 0x00040000-0x04437fff: front buffer (69600 kB)
(II) intel(0): 0x006ff000:            end of stolen memory
(II) intel(0): 0x04438000-0x04447fff: xaa scratch (64 kB)
(II) intel(0): 0x05000000-0x05ffffff: back buffer (15360 kB)
(II) intel(0): 0x06000000-0x06ffffff: depth buffer (15360 kB)
(II) intel(0): 0x07000000-0x08ffffff: DRI memory manager (32768 kB)
(II) intel(0): 0x09000000-0x0affffff: textures (32768 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xf91c0000
(II) intel(0): [drm] mapped SAREA 0xf91c0000 to 0xb7b90000
(II) intel(0): [drm] framebuffer handle = 0xe0040000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0xf3100000
(II) intel(0): [drm] ring buffer = 0xe0000000
(II) intel(0): [drm] init sarea width,height = 1920 x 1920 (pitch 2048)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x2c008000
(II) intel(0): [drm] Back Buffer = 0xe5000000
(II) intel(0): [drm] Depth Buffer = 0xe6000000
(II) intel(0): [drm] textures = 0xe9000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xe0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
   Screen to screen bit blits
   Solid filled rectangles
   8x8 mono pattern filled rectangles
   Indirect CPU to Screen color expansion
   Solid Horizontal and Vertical Lines
   Offscreen Pixmaps
   Setting up tile and stipple cache:
      32 128x128 slots
      32 256x256 slots
      16 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): Current clock rate multiplier: 8
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x006ff000 (pgoffset 1791)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x04438000 (pgoffset 17464)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x05000000 (pgoffset 20480)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x06000000 (pgoffset 24576)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x09000000 (pgoffset 36864)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output TMDS-1 is connected to pipe A
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 487 x 137
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fi"
(**) Generic Keyboard: XkbLayout: "fi"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf91c0000 at 0xb7b90000
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(EE) intel(0): I830 Vblank Pipe Setup Failed 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1
(II) intel(0): xf86UnbindGARTMemory: unbind key 2
(II) intel(0): xf86UnbindGARTMemory: unbind key 3
(II) intel(0): xf86UnbindGARTMemory: unbind key 4
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.
```

---

### Post by paahtis75 on 2008-01-03
> **paahtis75 said:**
> Having same problems to connection GA-G33M-S2H to Sony KDF50E2010 via HDMI-HDMI or DVI-HDMI using onboard GMA3100. Tv and cable are ok because same system works with GF7600 almost out-of-the box:



Now get picture 720p/60 with following changes to xorg.conf [http://lists.freedesktop.org/archives/xorg/2007-December/031202.html](http://lists.freedesktop.org/archives/xorg/2007-December/031202.html)
Still having some problems when using ModeLine "1280x720" 74.25 1280 1390 1430 1648 720 725 732 752 bottom of picture is flickering. Can not get any picture with modelines from gft.

---

