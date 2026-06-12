---
title: "x86 64-bit Ubuntu 9.10 very low display resolution"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by techie.brandon on 2010-04-19
I purchased a lenovo G550 recently and immediately dumped the Windows OS for Ubuntu 9.10. The display is currently defaulting to 1366x768. From reading it looks as though this display can support both 16:9 and 16:10 aspects. I have ran through the xrandr commands attempting to set my resolution to something...anything bigger than 1366x7768 (I'm used to 1600x1200 from my old T61, so this is painfully small). As a test I am trying to get 1920 1200, from my xrandr results it looks like it should be within the lcd's range. xrandr commands failed on me as I have seen on a couple other intel based resolution problems. I don't fully understand the root of the problem and have not had any luck in my searches. So I have also attempted to manually create the xorg.conf file, not luck yet. Any help will receive 1 million internets from me :)


```

user@Home:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)Cantiga Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)Cantiga Graphics Controller Hardware Version 0.0
memory: 32704kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edidfail

```


```
user@Home:~/Desktop$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

```

```

user@home:~/Desktop$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1360x768       59.8  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
  1920x1200 (0x27c)  193.2MHz
        h: width  1920 start 2056 end 2256 total 2592 skew    0 clock   74.6KHz
        v: height 1200 start 1203 end 1209 total 1245           clock   59.9Hz

user@Home:~$ xrandr --verbose
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3b
	Timestamp:  16712
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
LVDS1 connected 1366x768+0+0 (0x40) normal (normal left inverted right x axis y axis) 344mm x 193mm
	Identifier: 0x3c
	Timestamp:  16712
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       1
	CRTCs:      1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID_DATA:
		00ffffffffffff0009e5820500000000
		01130103802213780a22c095564e8e26
		24505400000001010101010101010101
		010101010101411c56a0500016303020
		360058c1100000190000000f000a0000
		00000000000000000020000000fe0042
		4f45204f540a202020202020000000fe
		0048543135365758422d3130300a0061
	BACKLIGHT: 10 (0x0000000a)	range:  (0,10)
	Backlight: 10 (0x0000000a)	range:  (0,10)
	scaling mode:	Fullscreen
		supported: Non-GPU      Fullscreen   No scale     Aspect      
  1366x768 (0x40)   72.3MHz -HSync -VSync *current +preferred
        h: width  1366 start 1414 end 1446 total 1526 skew    0 clock   47.4KHz
        v: height  768 start  771 end  777 total  790           clock   60.0Hz
  1360x768 (0x41)   84.8MHz -HSync +VSync
        h: width  1360 start 1432 end 1568 total 1776 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1024x768 (0x42)   94.5MHz +HSync +VSync
        h: width  1024 start 1072 end 1168 total 1376 skew    0 clock   68.7KHz
        v: height  768 start  769 end  772 total  808           clock   85.0Hz
  1024x768 (0x43)   78.8MHz +HSync +VSync
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.0KHz
        v: height  768 start  769 end  772 total  800           clock   75.0Hz
  1024x768 (0x44)   75.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1328 skew    0 clock   56.5KHz
        v: height  768 start  771 end  777 total  806           clock   70.1Hz
  1024x768 (0x45)   65.0MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  832x624 (0x46)   57.3MHz -HSync -VSync
        h: width   832 start  864 end  928 total 1152 skew    0 clock   49.7KHz
        v: height  624 start  625 end  628 total  667           clock   74.6Hz
  800x600 (0x47)   56.3MHz +HSync +VSync
        h: width   800 start  832 end  896 total 1048 skew    0 clock   53.7KHz
        v: height  600 start  601 end  604 total  631           clock   85.1Hz
  800x600 (0x48)   50.0MHz +HSync +VSync
        h: width   800 start  856 end  976 total 1040 skew    0 clock   48.1KHz
        v: height  600 start  637 end  643 total  666           clock   72.2Hz
  800x600 (0x49)   49.5MHz +HSync +VSync
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x4a)   40.0MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  800x600 (0x4b)   36.0MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock   35.2KHz
        v: height  600 start  601 end  603 total  625           clock   56.2Hz
  640x480 (0x4c)   36.0MHz -HSync -VSync
        h: width   640 start  696 end  752 total  832 skew    0 clock   43.3KHz
        v: height  480 start  481 end  484 total  509           clock   85.0Hz
  640x480 (0x4d)   31.5MHz -HSync -VSync
        h: width   640 start  664 end  704 total  832 skew    0 clock   37.9KHz
        v: height  480 start  489 end  492 total  520           clock   72.8Hz
  640x480 (0x4e)   31.5MHz -HSync -VSync
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x4f)   25.2MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   59.9Hz
  720x400 (0x50)   35.5MHz -HSync +VSync
        h: width   720 start  756 end  828 total  936 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  446           clock   85.0Hz
  640x400 (0x51)   31.5MHz -HSync +VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  400 start  401 end  404 total  445           clock   85.1Hz
  640x350 (0x52)   31.5MHz +HSync -VSync
        h: width   640 start  672 end  736 total  832 skew    0 clock   37.9KHz
        v: height  350 start  382 end  385 total  445           clock   85.1Hz
HDMI1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3d
	Timestamp:  16712
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
DP1 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3e
	Timestamp:  16712
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
DP2 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x3f
	Timestamp:  16712
	Subpixel:   unknown
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter:

user@Home:~/Desktop$ cvt 1920 1200 60
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

user@Home:~/Desktop$ xrandr --newmode "1920x1200"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync

user@Home:~/Desktop$ xrandr --addmode LVDS1 1920x1200
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  29
  Current serial number in output stream:  30

user@Home:~/Desktop$ xrandr --output LVDS1 --mode 1920x1200
xrandr: cannot find mode 1920x1200
```

My first attempt at the xorg.conf file is below; I believe I did something to generate the majority of this file, I did add the modelines for monitor and then modes for screen.
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
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
	Load  "extmod"
	Load  "dbe"
	Load  "glx"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	Modeline "1600x900"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
	Modeline "1920x1200"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
	Modeline "2560x1600"  348.50  2560 2760 3032 3504  1600 1603 1609 1658 -hsync +vsync
	Modeline "2736x1536"  355.75  2736 2936 3232 3728  1536 1539 1549 1592 -hsync +vsync
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
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
		Viewport   0 0
		Depth     24
		Modes	"2736x1536" "2560x1600" "1920x1200" "1600x900"
	EndSubSection
EndSection

```


Below is my second attempt, with almost all the misc info stripped out.
```

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync 24 - 82
	VertRefresh 50 - 75
	Modeline "1920x1200"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 16
	SubSection "Display"
		Depth 24
		Modes "1920x1200"
	EndSubSection
EndSection

```

I've gone out to the intel site to try and verify driver information but require privilege access to get the reference manual which looks like it should have information about supported modes. I have requested access, eta under 2 days.

[http://edc.intel.com/Software/Downloads/IEGD/#download](http://edc.intel.com/Software/Downloads/IEGD/#download)

Looking over my xorg.conf I notice that the monitor seems to be unknown, not sure if that is relevant, from other posts I tend to think not. 

I've been working with this issue on and off for a month now, would be good to know if is even possible given my hardware.

---

### Post by techie.brandon on 2010-04-20
Update added to first post

---

### Post by techie.brandon on 2010-04-20
update moved into first post

---

### Post by techie.brandon on 2010-05-04
*bump* ??

---

### Post by efflandt on 2010-05-05
The native resolution of your laptop display is 1366x768, and from what you posted, it does not appear that you have an external display connected (LVDS1 is your laptop display and X says nothing else is connected).  So it is unclear what you are trying to achieve by trying to force your laptop display to a higher resolution than it is.

If you want higher resolution, you either need a different laptop, or an external display (a 32" 1080p HDTV works well).  If you want to get more text on the screen, you can change font sizes in System > Preferences > Appearance.

---

