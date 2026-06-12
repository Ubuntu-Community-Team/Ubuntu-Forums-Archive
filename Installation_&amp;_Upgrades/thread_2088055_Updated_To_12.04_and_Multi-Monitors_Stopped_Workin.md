---
title: "Updated To 12.04 and Multi-Monitors Stopped Working"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by MultipleMonomials on 2012-11-25
I used to have a multi-monitor setup that was fine--on Windows.  When I began using Linux, I had to use Xrandr to get it working for my ATI Radeon HD 5500.  I added 
    ```
xrandr --newmode "1400x900_60.00"  103.50  1400 1480 1624 1848  900 903 913 934 -hsync +vsync

    xrandr --addmode DFP2 1400x900_60.00

    xrandr --output DFP2 --mode 1400x900_60.00

    xrandr --addmode CRT2 1400x900_60.00

    xrandr --output CRT2 --mode 1400x900_60.00
```
 to /etc/gdm/Init/Default, now the 1440 x 900 resolution was an option.  But if I tried to set it to extended dekstop, I got an error about my monitor resolution being bigger than my selected resolution.  So I changed Xorg.conf to this:
```
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		[COLOR="Red"]Virtual	3000 900[/COLOR]
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection
```

That worked perfectly when I was using 10.04.  Now that I upgraded to 12.04, the changes to init/Default carried over, but the Xorg.conf got reverted.  So I added them back.  No dice.  When I try to set extended desktop, I get the error [ATTACH]227721[/ATTACH].  I tried Catalyst Control, but it crashes as soon as I try to change anything.  Any ideas?

---

