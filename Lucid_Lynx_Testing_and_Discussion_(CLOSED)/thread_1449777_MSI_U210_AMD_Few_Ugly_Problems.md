---
title: "MSI U210 AMD Few Ugly Problems"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by iamtrump on 2010-04-08
Hi! I have MSI U210 netbook with AMD Neo processor and ATI Radeon X1250 graphic card. I installed Ubuntu 10.04 amd64 version. And there is few problems.

1. When I unplug AC adapter the notification about critical battery level appears, but by battery is charged and the battery indicator shows me that 1 hour remains! Then netbook goes to sleep.

2. When I connect external monitor via VGA image on that flickers. I tried to change Virtual parameter in my xorg.conf but it was usless. See current xorg.conf.
> Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
EndSection

Section "Files"
	ModulePath   "/opt/xorg/lib/xorg/modules,/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "record"
	Load  "dbe"
	Load  "glx"
	Load  "dri2"
	Load  "extmod"
EndSection

Section "Monitor"
	#DisplaySize	  270   150	# mm
	Identifier   "Monitor0"
	VendorName   "HSD"
	ModelName    "HSD121PHW1"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RS690M [Radeon X1200 Series]"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Virtual	4000 2000
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Please help me!

---

### Post by Trenchbroom on 2010-04-12
I have an MSI Wind U100 with the same battery issue.  The icon indicates battery is fully charged but as soon as I unplug the A/C power it tells me that "laptop battery critically low" and then hibernates within 30 seconds.  However the icon still says 99.4% charged.

---

