---
title: "Festy - doesn't boot and X crashes"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by TheHammer on 2007-04-19
hi, 

I upgraded today and now I've two problems:
1st:
X crashes instantly after (graphical) log in

Here's my xorg log

```

xauth:  creating new authority file /home/thehammer/.serverauth.6519 


X Window System Version 7.2.0 
Release Date: 22 January 2007 
X Protocol Version 11, Revision 0, Release 7.2 
Build Operating System: Linux Ubuntu 
Current Operating System: Linux TheHammer 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 
Build Date: 04 April 2007 
   Before reporting problems, check http://wiki.x.org 
   to make sure that you have the latest version. 
Module Loader present 
Markers: (--) probed, (**) from config file, (==) default setting, 
   (++) from command line, (!!) notice, (II) informational, 
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Apr 19 18:40:07 2007 
(==) Using config file: "/etc/X11/xorg.conf" 
The XKEYBOARD keymap compiler (xkbcomp) reports: 
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols 
>                   Ignoring extra symbols 
Errors from xkbcomp are not fatal to the X server 
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list! 
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list! 
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list! 

Backtrace: 
0: /usr/bin/X11/X(xf86SigHandler+0x81) [0x80c5d91] 
1: [0xffffe420] 
2: /usr/lib/libXfont.so.1(FontFileFreeTable+0x37) [0xb7ef3997] 
3: /usr/lib/libXfont.so.1(FontFileFreeDir+0x25) [0xb7ef39e5] 
4: /usr/lib/libXfont.so.1(FontFileFreeFPE+0x2d) [0xb7ef6fbd] 
5: /usr/bin/X11/X [0x808d249] 
6: /usr/bin/X11/X [0x808d2b6] 
7: /usr/bin/X11/X [0x808da8c] 
8: /usr/bin/X11/X(ProcSetFontPath+0xa5) [0x8086785] 
9: /usr/bin/X11/X [0x8142531] 
10: /usr/bin/X11/X(Dispatch+0x19f) [0x808c61f] 
11: /usr/bin/X11/X(main+0x495) [0x8074785] 
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d6debc] 
13: /usr/bin/X11/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1] 

Fatal server error: 
Caught signal 11.  Server aborting 

xinit:  connection to X server lost.

```

and my xorg.conf:
```
Section "Files" 
  FontPath "/usr/share/X11/fonts/misc" 
  FontPath "/usr/share/X11/fonts/cyrillic" 
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled" 
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled" 
  FontPath "/usr/share/X11/fonts/Type1" 
  FontPath "/usr/share/X11/fonts/100dpi" 
  FontPath "/usr/share/X11/fonts/75dpi" 
  FontPath "/usr/share/fonts/X11/misc" 
  # path to defoma fonts 
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" 
EndSection 

Section "Module" 
  Load "i2c" 
  Load "bitmap" 
  Load "ddc" 
  Load "extmod" 
  Load "freetype" 
  Load "int10" 
  Load "type1" 
  Load "vbe" 
  load "glx" 
  load "v4l" 
EndSection 

Section "InputDevice" 
  Identifier "Generic Keyboard" 
  Driver "kbd" 
  option "CoreKeyboard" 
  option "XkbRules" "xorg" 
  option "XkbModel" "pc105" 
  option "XkbLayout" "de" 
  option "XkbOptions" "lv3:ralt_switch" 
  option "XkbVariant" "nodeadkeys" 
EndSection 

Section "InputDevice" 
  Identifier "Configured Mouse" 
  Driver "mouse" 
  option "CorePointer" 
  option "Device" "/dev/input/mice" 
  option "Protocol" "ExplorerPS/2" 
  option "ZAxisMapping" "4 5" 
  option "Emulate3Buttons" "false" 
EndSection 

Section "InputDevice" 
  Driver "wacom" 
  Identifier "stylus" 
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus" 
  option "ForceDevice" "ISDV4"# Tablet PC ONLY 
  # /dev/input/event 
  # for USB 
EndSection 

Section "InputDevice" 
  Driver "wacom" 
  Identifier "eraser" 
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser" 
  option "ForceDevice" "ISDV4"# Tablet PC ONLY 
  # /dev/input/event 
  # for USB 
EndSection 

Section "InputDevice" 
  Driver "wacom" 
  Identifier "cursor" 
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor" 
  option "ForceDevice" "ISDV4"# Tablet PC ONLY 
  # /dev/input/event 
  # for USB 
EndSection 



Section "DRI" 
  Mode 0666 
EndSection 


Section "ServerFlags" 
  option "Xinerama" "true" 
EndSection 

################################## 
Section "Device" 
  identifier "NVIDIA Corporation [GeForce]0" 
  boardname "nv" 
  busid "PCI:1:0:0" 
  driver "nvidia" 
  screen 0 
EndSection 

Section "Device" 
  identifier "NVIDIA Corporation [GeForce]1" 
  boardname "nv" 
  busid "PCI:1:0:0" 
  driver "nvidia" 
  screen 1 
EndSection 

Section "Monitor" 
  identifier "Monitor0" 
  vendorname "Generic" 
  modelname "1600x1200 @ 76 Hz" 
  #HorizSync 31.5-94.0 
  #VertRefresh 50-90 
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync 
  .............. 
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync 
  gamma 1.0 
EndSection 

Section "Monitor" 
  identifier "Monitor1" 
  vendorname "Generic" 
  modelname "1600x1200 @ 76 Hz" 
  #HorizSync 31.5-94.0 
  #VertRefresh 50-90 
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync 
........................ 
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync 
  
  gamma 1.0 
EndSection 

Section "Screen" 
  Identifier "Screen0" 
  Device "NVIDIA Corporation [GeForce]0" 
  Monitor "Monitor0" 
  DefaultDepth 24 
  SubSection "Display" 
    depth 24 
    modes "1152x864@100" 
  EndSubSection 
EndSection 

Section "Screen" 
  Identifier "Screen1" 
  Device "NVIDIA Corporation [GeForce]1" 
  Monitor "Monitor1" 
  DefaultDepth 24 
  SubSection "Display" 
    depth 24 
    modes "1152x864@100" 
  EndSubSection 
EndSection 

#Section "Extensions" 
#   Option "Composite" "Enable" 
#EndSection 

Section "ServerLayout" 
  Identifier "Default Layout" 
  screen 0 "Screen0" 0 0 
  screen 1 "Screen1" rightof "Screen0" 
  InputDevice "Generic Keyboard" 
  InputDevice "Configured Mouse" 
  option "Xinerama" "on" 
EndSection
```

2nd:
Festy doesn't boot anymore, except with the recovery kernel and I don't know why :(

here is my colsole output:

[ 35.xxxxxx ] ata3.00 failed to set xfermode (err_mask 0x40) 
[ 70.xxxxxx ] ata3.00 failed to set xfermode (err_mask 0x40) 
[ 105.xxxxx ] ata3.00 failed to set xfermode (err_mask 0x40) 
........
Alert! /dev/disk/by-uuid/--{[0-9a-z-]*(you know it}-- does not exist, dropping to shell. 
... debian buldin shell (ash)  ... 

that's it

there is no folder  /dev/disk/by-uuid , but  
in by-id/ are some files with ...usb-generic-... and  
in by-path/ are some files like:  pci-000:00:1a_7-usb_0:2:1:0-scsi-0:0:0
pci-000:00:1a_7-usb_0:2:1:0-scsi-0:0:1 to 3

---

### Post by HKalnes on 2007-04-19
There are already 2 threads about the X problem. I got  solved my issue here:
[http://ubuntuforums.org/showthread.php?t=413713]("http://ubuntuforums.org/showthread.php?t=413713")

---

### Post by TheHammer on 2007-04-19
sorry, festy doesn't boot anymore witch the recovery kernel,

but the output is better: 
```


ata3.00: qc time out (cmd 0x27) 
ata3.00: ata_hpu_resize 1: sectors: 625142448, hpa sectors=0 
ata3.00: ATA-7 ST332060AS, 3.AAE, max UDMA/133 
ata3.00: 625142448 sectors, multi; 16 LBA48, NCQ (depth 0/32) 
ata3.00: failed to set xfermod (err_mask 0x40) 
... 
ATA abnormal status 0x7f on port  0x0001f107 
... 

```

Tomorrow, I'll install festy again, but I would like to know why.

---

### Post by noerrorsfound on 2007-04-21
This happened to me after upgrading to 7.04.

All I had to do was reinstall the NVIDIA proprietary drivers. I could also fix the error by switching to the non-proprietary drivers but since I play games I prefer the ones from NVIDIA.

---

