---
title: "ubuntu 12.04  with AMD Radeon HD 7400M Series  refresh rate  issue  ---maximum is 60"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by sgm277 on 2012-09-28
Hi all,

I found I can't change the refresh rate of AMD Radeon HD 7400M Series, the maximun is 60 which hurt my eyes. I searched long time and couldn't make it higher like 75.

Below is the detail:

root@admin:/etc/X11# xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+   40.0  
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


root@admin:/etc/X11# more xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
        Option      "EnableRandR12" "false"
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


Your help will be highly appreciated.

---

### Post by Wim Sturkenboom on 2012-09-28
Make and model of monitor please. If it's a laptop, the same question ;)

PS
As your current resolution is 1366x768, I suspect that to be the max resolution of the screen and I also suspect that you will not be able to go higher than 60Hz in that case.

---

### Post by Starcruiser322 on 2012-09-28
Do you have the proprietary AMD Catalyst package? It solved A LOT of problems for me and gives stats like monitor max refresh rate reported (60 hz for me).

---

### Post by sgm277 on 2012-09-28
> **Starcruiser322 said:**
> Do you have the proprietary AMD Catalyst package? It solved A LOT of problems for me and gives stats like monitor max refresh rate reported (60 hz for me).

yes, I have installed newest driver and AMD Catalyst package. My graphic card is ATI HD 7450M.

---

### Post by sgm277 on 2012-09-28
> **Wim Sturkenboom said:**
> Make and model of monitor please. If it's a laptop, the same question ;)

PS
As your current resolution is 1366x768, I suspect that to be the max resolution of the screen and I also suspect that you will not be able to go higher than 60Hz in that case.


Yes, it is a laptop, Dell N4050.

---

### Post by Wim Sturkenboom on 2012-09-29
OK, specs say that 1366x768 is the max resolution. Usually this implies that you will not be able to use higher vertical refresh rates. The only way is to reduce the resolution which _maybe_ will allow to increase the vertical refresh rate.

Also, this is a lcd/led/tft and not a CRT. Refresh rate of 60 Hz on those should not hurt your eyes. It might be that fonts are too small to be comfortable to read?

---

### Post by sgm277 on 2012-09-29
> **Wim Sturkenboom said:**
> OK, specs say that 1366x768 is the max resolution. Usually this implies that you will not be able to use higher vertical refresh rates. The only way is to reduce the resolution which _maybe_ will allow to increase the vertical refresh rate.

Also, this is a lcd/led/tft and not a CRT. Refresh rate of 60 Hz on those should not hurt your eyes. It might be that fonts are too small to be comfortable to read?


Hi Wim,

Thank you for your prompt help, this is the first time I am using ubuntu insteading of Windows, In my impression, when using windows, I can set the refresh rate to 75. So I think there must be a way to set the laptop refresh rate to 75 in ubuntu also. For now I don't feel any uncomfortable,but for the long term, I am worring about my eyes :)

---

### Post by Wim Sturkenboom on 2012-09-29
Are you running dual boot? That would be the easy way to check. Untill proven wrong, I'm quite confident that "my thoughts" are more correct than "your impression" ;)

---

### Post by sgm277 on 2012-09-29
> **Wim Sturkenboom said:**
> Are you running dual boot? That would be the easy way to check. Untill proven wrong, I'm quite confident that "my thoughts" are more correct than "your impression" ;)

No dual boot, I only installed ubuntu .

---

