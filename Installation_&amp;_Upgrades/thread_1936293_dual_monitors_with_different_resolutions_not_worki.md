---
title: "dual monitors with different resolutions not working (nvidia)"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by plablo09 on 2012-03-05
Hi, I've searched the forums to no avail. My problem is as follows:
I'm setting up a new system, I have two monitors, the main one is working fine, but when I activate the second monitor through nvidia-settings it doesn't display an option with the right resolution (that would be 1440x900) so I end up wit a ugly looking second monitor. 

My graphics card is:
Nvidia GeForce GTS 450

My xorg.conf:
```

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Samsung SA300/SA350"
	HorizSync       30.0 - 81.0
	VertRefresh     56.0 - 75.0
	Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "TwinView" "1"
	Option         "TwinViewXineramaInfoOrder" "DFP-0"
	Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidi
a-auto-select +1920+0"

	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
	Option         "Xinerama" "0"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce GTS 450"
	Option     "MetaModes" "1440x900"
	Option	"NoLogo"	"True"
EndSection

```
Running xrandr gives:
```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 3200 x 1080, current 3200 x 1080, maximum 3200 x 1080
default connected 3200x1080+0+0 0mm x 0mm
   3200x1080      50.0*

```
I've tried some workarounds but I'm not quite there yet. Any help is appreciated

---

### Post by papibe on 2012-03-05
What kind of connection are you using for your monitors (vga, dvi, hdmi, etc)?

Does the 2nd one work while used alone? (1st monitor not connected).

Regards.

EDIT: the reason I asked is that some monitors can report bad/corrupt EDID while used over VGA but work fine using DVI (for example).

---

### Post by plablo09 on 2012-03-05
Thanks!
The main monitor is connected to a dvi port, the second is connected to a hdmi trough a vga adapter. And yes, the second works alone (trough dvi).

---

### Post by papibe on 2012-03-05
Then there are some options.

This is what I would do:
[LIST=1]
[*]Boot with 2nd monitor using the DVI cable.
[*]Using the 'Nvidia X Server Settings' get its EDID information on a file.
[*]To do that go to  GPU 0 -> Adquire EDID.
[*]Then reboot using the monitors as you want them to be.
[*]Run on a terminal the Nvidia Settings called as root:
```
gksudo nvidia-settings
```
[*]Set the monitor as close as you want as possible (regardless of a bad resolution, try going safe like a low res).
[*]Save the current configuration by going to X Server Display Configuration -> Save to X Configuration file.
[*]Now edit your X configuration that you just save by running in a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```
[*]Look for a section called "Screen" that is the one used for the second monitor. Add this line inside that section:
```
Option	"CustomEDID" "CRT-0:/path/to/edid.bin"
```
change CRT-0 for the name nvidia gave to the second monitor (for instance CRT-0, CRT-1, DFP-0, HDMI-0, etc).
edid.bin is the file you just obtained on step 2. Use an absolute path to it.
Save the file.
[*]Restart you machine and try to set the correct resolution this time.
[/LIST]
Hope it helps, and tell us how it goes.
Regards.

---

### Post by plablo09 on 2012-03-05
Thanks a lot papibe!

It almost works, when I restart the second time (after setting the option "CustomEDID"), the second monitor is set at the right resolution (1440x900), but when I logged in there where errors about not being able to set some metamodes. I'll check to see the exact error messages.
In the meantime, I have to go, but i'll report tomorrow

---

### Post by plablo09 on 2012-03-08
Sorry about thin late reply, I got caught up with work. 
The procedure sketched by papibe effectively solved the issue (after I manually removed some metamodes from xorg.conf), so I'm marking this as solved
Thanks a lot

---

