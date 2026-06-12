---
title: "driver for nVidia Corporation C51G [GeForce 6100] (rev a2)"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by Pocko on 2011-07-15
Hello,
that is my first post here (new in Linux at all)
I have the following problem. I've just install Kubuntu 11.04 but my screen dancing like in 15 Hz... I tried to install drivers offered by Additional Drivers wizard but after reboots the situation is the same. Please for some help about what to do. I'll also ask for correct command lines because I'm not so familiar with that yet. 
Cheers

---

### Post by Grenage on 2011-07-15
Greetings;

When you say that it's dancing about, could you elaborate?

Is the resolution correct?
What kind of monitor do you have?
Are you using nvidia-settings?

Failing that, please post your monitor make and model, and the contents of this file:

/etc/X11/xorg.conf

You should be able to browse to it from any text editor, whatever Kubuntu may use by default.

---

### Post by Pocko on 2011-07-15
I thing this "dancing" is because of the frequency. I guess it's from driver.  
Cause the PC is almost dead cant post any PrintScreans...

The monitor is Acer, AL1723
The resolution is 1280 x 1024 - and it looks good
I don't know if I'm using NVidia settings :(

The content of /etc/X11/xorg.conf is:
[I]Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection[/I]

thanks

---

### Post by Grenage on 2011-07-15
> **Pocko said:**
> I thing this "dancing" is because of the frequency. I guess it's from driver.  
Cause the PC is almost dead cant post any PrintScreans...

The monitor is Acer, AL1723
The resolution is 1280 x 1024 - and it looks good
I don't know if I'm using NVidia settings :(

The content of /etc/X11/xorg.conf is:
[I]Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection[/I]

thanks

Try this xorg.conf; you can edit the file via the GUI using:

```
gksu gedit /etc/X11/xorg.conf
```

or from a CLI:

```
sudo vim /etc/X11/xorg.conf
```

Here we go:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "ACER"
	ModelName "AL1723"
	HorizSync 30 - 65
	VertRefresh 50 - 75
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "GeForce 6100"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

If that doesn't work, try:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "ACER"
	ModelName "AL1723"
	HorizSync 30 - 65
	VertRefresh 50 - 75
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "nvidia"
	VendorName "GeForce 6100"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

---

