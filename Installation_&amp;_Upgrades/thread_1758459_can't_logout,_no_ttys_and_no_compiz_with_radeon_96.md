---
title: "can't logout, no ttys and no compiz with radeon 9600 after update to 11.04"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by heliogabalus on 2011-05-14
hello, i'm not very good at this graphics stuff, i'd love to get some assistance. the computer is an old powerbook G4 15''.

i successfully updated to 11.04 (one of the less troublesome updates so far). unfortunately, neither unity nor compiz are working (i'll leave the log and my xorg.conf below). i also tried without any xorg.conf file and had the same problem. also tried with a auto generated file and had the same problem. before the update i had compiz running perfectly, using the xorg.conf below.

also, whenever i logout or use "ctrl+alt+f1" to change to a text tty i don't get anything. on both cases i get a blank screen, and doing "ctrl-alt" back to X doesn't work. 

this doesn't happen if X is not running (i started the system without X and could use all ttys and so on).

i suspect it is all connected to some bad X conf that i might have, but as i said, i don't know much about this. 

i would really appreciate some help, thank you all in advance!

errors from compiz 
```
 compiz --replace --debug
compiz (core) - Debug: Could not stat() file /home/h/.compiz-1/plugins/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /usr/lib/compiz/libcore.so : No such file or directory
compiz (core) - Debug: Could not stat() file /home/h/.compiz-1/plugins/libccp.so : No such file or directory
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
(... some 20 lines like this one)
compiz (core) - Debug: Could not stat() file /home/h/.compiz-1/plugins/libbailer.so : No such file or directory
Initializing bailer options...done
compiz (core) - Debug: Could not stat() file /home/h/.compiz-1/plugins/libdetection.so : No such file or directory
Initializing detection options...done
compiz (core) - Debug: Could not stat() file /home/h/.compiz-1/plugins/libcomposite.so : No such file or directory
Initializing composite options...done
compiz (core) - Debug: Could not stat() file /home/h/.compiz-1/plugins/libopengl.so : No such file or directory
Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected
Compiz (bailer) - Info: Ensuring a shell for your session

```

xorg.conf
```

Section "Device"
    Identifier    "Radeon 9600"
    Driver        "ati"
    BusID        "PCI:0:16:0"
    Option        "DynamicClocks" "true"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "true"
    Option        "UseFBDev" "false"
    Option        "DRI" "true"
    Option        "GARTSize" "64"
    Option        "AddARGBGLXVisuals" "true"
    Option        "XAANoOffscreenPixmaps"
    Option        "DisableGLXRootClipping" "true"
    Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Radeon 9600"
    Monitor        "Configured Monitor"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

```

xorg.conf.new generated automatically
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
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
	Load  "extmod"
	Load  "record"
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
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "Dac8Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "CPPIOMode"          	# [<bool>]
        #Option     "CPusecTimeout"      	# <i>
        #Option     "AGPMode"            	# <i>
        #Option     "AGPFastWrite"       	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "RingSize"           	# <i>
        #Option     "BufferSize"         	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "NoBackBuffer"       	# [<bool>]
        #Option     "DMAForXv"           	# [<bool>]
        #Option     "FBTexPercent"       	# <i>
        #Option     "DepthBits"          	# <i>
        #Option     "PCIAPERSize"        	# <i>
        #Option     "AccelDFS"           	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
        #Option     "CustomEDID"         	# [<str>]
        #Option     "DisplayPriority"    	# [<str>]
        #Option     "PanelSize"          	# [<str>]
        #Option     "ForceMinDotClock"   	# <freq>
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "RageTheatreCrystal" 	# <i>
        #Option     "RageTheatreTunerPort" 	# <i>
        #Option     "RageTheatreCompositePort" 	# <i>
        #Option     "RageTheatreSVideoPort" 	# <i>
        #Option     "TunerType"          	# <i>
        #Option     "RageTheatreMicrocPath" 	# <str>
        #Option     "RageTheatreMicrocType" 	# <str>
        #Option     "ScalerWidth"        	# <i>
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
        #Option     "MacModel"           	# <str>
        #Option     "TVDACLoadDetect"    	# [<bool>]
        #Option     "ForceTVOut"         	# [<bool>]
        #Option     "TVStandard"         	# <str>
        #Option     "IgnoreLidStatus"    	# [<bool>]
        #Option     "DefaultTVDACAdj"    	# [<bool>]
        #Option     "Int10"              	# [<bool>]
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "ATOMTVOut"          	# [<bool>]
        #Option     "R4xxATOM"           	# [<bool>]
        #Option     "ForceLowPowerMode"  	# [<bool>]
        #Option     "DynamicPM"          	# [<bool>]
        #Option     "NewPLL"             	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:0:16:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card1"
	Driver      "fbdev"
	BusID       "PCI:0:16:0"
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
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
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
	EndSubSection
EndSection


```

lspci output

```

lspci | grep VGA
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

---

### Post by heliogabalus on 2011-05-15
just an update on this issue: i can't hibernate the computer (i could on 10.10). i also get the same issues logging out in other window managers (like E17 or fluxbox). all of them crash my screen and i stop being able to use it.

---

### Post by heliogabalus on 2011-05-18
bump, or should i just file a bug? where could i do that?

---

