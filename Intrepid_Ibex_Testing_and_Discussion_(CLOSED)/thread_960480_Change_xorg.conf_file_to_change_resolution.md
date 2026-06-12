---
title: "Change xorg.conf file to change resolution"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eekfonky on 2008-10-27
I have recently installed 8.10 and installed the Nvidia driver 173 from the hardware drivers. However my resolution has been reduced from 1280x1024 to 640x480. I cannot work like this and would appreciate any help to edit the correct file to permanently change this back to 1280x1024. I have an Acer AL1716 A monitor.

Please help

---

### Post by wizard10000 on 2008-10-27
> **eekfonky said:**
> I have recently installed 8.10 and installed the Nvidia driver 173 from the hardware drivers. However my resolution has been reduced from 1280x1024 to 640x480. I cannot work like this and would appreciate any help to edit the correct file to permanently change this back to 1280x1024. I have an Acer AL1716 A monitor.

Please help

First, try this -

sudo dpkg-reconfigure xserver-xorg

and see if you can add the 1280x1024 resolution there.  If that doesn't work, back up your existing /etc/X11/xorg.conf and add this to the "Monitor" section in the file - you'll need to be root to do it, though.

```
ModeLine       "1280x1024" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
```

Hope this helps -

---

### Post by eekfonky on 2008-10-27
My computer will now only start in low-graphics mode. Thanks anyway. I think my EDID is wrong and my nvidia driver makes things worse!!
Any ideas?

---

### Post by eekfonky on 2008-10-27
here is my xorg as it stands
```
Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Acer"
	Model Name	"AL1716"
	HorizSync       31.0 - 81.0
    	VertRefresh     56.0 - 75.0
	Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Monitor0"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

It has to start in low graphics mode due to parsing error??

---

### Post by godsbane on 2008-10-28
I am having a similar issue with my resolution not being identified correctly.

```
Section "Monitor"
	Identifier	"Configured Monitor"
# 1600x1200 @ 85.00 Hz (GTF) hsync: 107.10 kHz; pclk: 234.76 MHz
Modeline "1600x1200"  234.76  1600 1720 1896 2192  1200 1201 1204 1260  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Depth     24
		Modes    "1600x1200"
	EndSubSection

EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

That is my xorg.conf

Nothing I do lets me go above 1025x768 @ 58hz(wtf?)
Have used a similar setup since 6.10... and i cannot for the life of me get this working.

Also, was getting the parsing error, but found that my quotes for my modeline were other symbols when i opened it in nano, fixed them, and it booted up no problem after that.

---

### Post by andrewabc on 2008-10-28
> **wizard10000 said:**
> First, try this -

sudo dpkg-reconfigure xserver-xorg



I thought that hasn't worked since Gutsy?

---

### Post by sdowney717 on 2008-10-28
why is 640 by 480 the universal failure resolution mode?
it is impossible to use.
why not 800 by 600!

what happens if you run an empty xorg.conf?
xorg is supposed to autoconfigure itself then.

open up /var/log/xorg log and see what it says about errors and monitor detection.

---

### Post by eekfonky on 2008-10-29
All I want to know is will the problem be fixed for 8.10? Does anyone out there know?

---

### Post by andrewabc on 2008-10-29
> **eekfonky said:**
> All I want to know is will the problem be fixed for 8.10? Does anyone out there know?

Your best bet would be download the livecd when it comes out. You could also try the kubuntu and xubuntu livecd to see if they have the same problem.

So the resolution problem occurred when you updated the drivers? With a default install it worked fine?

---

### Post by eekfonky on 2008-10-29
I'll try that and let you know tomorrow as soon as I've got 8.10 installed

---

