---
title: "Problem Mobility Radeon HD 5400 Series. Ubuntu Precise 64bits"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by unskold on 2012-04-05
good afternoon

I do not know what else to try. I'm about to leave the ubuntu because I can not in any way to install the driver of my graphics to take 3D acceleration.

**lspci -nn | grep VGA**:
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] [1002:68e0]

I tried to install with jockey yet if i make the command fglrxinfo:

> X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

**xorg.conf **:

> Section "Screen"
   Identifier   "Default Screen"
   DefaultDepth   24
EndSection

Section "Module"
   Load   "glx"
EndSection
ps: whenever I tried to change this is the computer does not start, just a black screen and can only start putting back the xorg as it was, through the command line

I tried installing the latest proprietary drivers manually and get the same result. that is a black screen and the pc does not start.
xorg when I do sudo aticonfig - initial-f - adapter = all is:
> Section "ServerLayout"
   Identifier     "aticonfig Layout"
   Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
   Load  "glx"
EndSection

Section "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   Option       "VendorName" "ATI Proprietary Driver"
   Option       "ModelName" "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver      "fglrx"
   BusID       "PCI:1:0:0"
EndSection

Section "Screen"
   Identifier "Default Screen"
   DefaultDepth     24
EndSection

Section "Screen"
   Identifier "aticonfig-Screen[0]-0"
   Device     "aticonfig-Device[0]-0"
   Monitor    "aticonfig-Monitor[0]-0"
   DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
      Depth     24
   EndSubSection
EndSection

ps: with this configuration the pc did not start, i get black screen again. So I suppose the problem is in xorg file, i think it does not detect well what is the graphic card or something...

Thanks

---

### Post by Paddy Landau on 2012-04-06
Looking at Google, it appears that your specific card is not well supported under Linux.

However, you are using 12.04, which is still in beta. Have you tried Ubuntu 11.10? Load it from a Live USB and test.

You may have to purchase a supported card or use Windows or Mac instead.

Sorry I am not much help.

---

### Post by unskold on 2012-04-06
hi. unfortunately i use a laptop. is not an option to buy another graphics card...

Yes i already experienced the 11.10 not results...

---

