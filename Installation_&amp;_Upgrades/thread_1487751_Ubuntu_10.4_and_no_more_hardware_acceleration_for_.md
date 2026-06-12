---
title: "Ubuntu 10.4 and no more hardware acceleration for ATI Mobility Radeon X1400"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by puccio on 2010-05-19
Hi,

I upgraded from Ubuntu 9.10 to Ubuntu 10.4.

I'm using the driver **radeonhd** (it seems to be the best one for my ATI Mobility Radeon X1400 as far as the package description says), and my graphical experience is pretty slow, for example when I scroll windows, reduce them, etc..

Please note that if I try to use the "generic" **radeon** driver, Xorg does *not* start.

Here it is indeed the output of **glxinfo**:

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_MESA_copy_sub_buffer
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.7.1
OpenGL shading language version string: 1.20
OpenGL extensions:

```


and it is my **xorg.conf**


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
	Load  "glx"
	Load  "dri2"
	Load  "dri"
	Load  "extmod"
	Load  "dbe"
	Load  "record"
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
	#DisplaySize	  330   210	# mm
	Identifier   "Monitor0"
	VendorName   "SEC"
	ModelName    "0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
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
        #Option     "ShowCache"          	# [<bool>]
        #Option     "ClockGating"        	# [<bool>]
        #Option     "VGAAccess"          	# [<bool>]
        #Option     "ReverseDDC"         	# [<bool>]
        #Option     "LVDSProbePLL"       	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# [<bool>]
        #Option     "ConnectorTable"     	# <str>
        #Option     "DefaultConnectorTable" 	# [<bool>]
        #Option     "DefaultTMDSPLL"     	# [<bool>]
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
	Driver      "radeonhd"
    Option      "DRI" "on"
    #Option      "AccelMethod" "exa"
    #Option      "EXANoComposite" 
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon Mobility X1400"
	BusID       "PCI:1:0:0"
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

Section "DRI"
    Mode         0666
EndSection

```

thanks in advance for any help!

---

### Post by rgm3 on 2010-06-03
I don't have any constructive help -- it seems nobody does.  Suggestions I've seen are to run an older X server that is compatible with the older Catalyst drivers, but this is... sub-optimal.

Off-site commiseration:
[http://www.phoronix.com/forums/showthread.php?t=22161#post114159](http://www.phoronix.com/forums/showthread.php?t=22161#post114159)

On-site "me too"s:
[http://swiss.ubuntuforums.org/showthread.php?p=9309646](http://swiss.ubuntuforums.org/showthread.php?p=9309646)

Ubuntu 10.4 Lucid Lynx uses xorg version 7.5+ubuntu, but the Catalyst drivers for the X1400 seem to stop at xorg 7.4.
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=us&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.9&lang=us&rev=9.3&ostype=Linux%20x86)

Note that the X1400 isn't specifically mentioned on that list, but the X1300 and X1550 are, so it could be that that isn't the right link for the Catalyst drivers.  Maybe the X1400 was OEM only.  *shrug*

---

### Post by libertao on 2010-06-09
> **rgm3 said:**
> Suggestions I've seen are to run an older X server that is compatible with the older Catalyst drivers, but this is... sub-optimal.


When you say "sub-optimal" do you mean so because it still doesn't run well, it's a cumbersome operation, or because you don't want to have an older X server running?  Debating whether to do this.

---

### Post by rgm3 on 2010-06-11
> **libertao said:**
> When you say "sub-optimal" do you mean so because it still doesn't run well, it's a cumbersome operation, or because you don't want to have an older X server running?  Debating whether to do this.

Sub-optimal for me for the following reasons:

1) takes work to do (I know, "wah")
2) Old stuff is old
3) new stuff is shiny and new

It might run beautifully, I do plan to try it eventually.  I expect that I'd have to exclude xorg from future updates though, and go through a rigamarole again in 6 months when I update or fresh install 10.10 Maverick Meerkat.

There's a tiny chance that some day the radeonhd driver will improve.  Until then, I guess I'll have to deal with certain glx-dock applets crashing my X-server and other such weirdness.

At least full-screen video runs okay for me (if I choose the right output), full-screen flash too.

---

### Post by libertao on 2010-06-13
> **rgm3 said:**
> 

At least full-screen video runs okay for me (if I choose the right output), full-screen flash too.

Yeah I can run full screen video on it, but I wanted to turn this older laptop (not really THAT old) into a media center for my tv, but the video card can't output properly (it's a wavy mess) and xbmc menus and cursor are incredibly laggy.  Maybe if I find some time I'll try that workaround, but like you said, sounds a bit of a pain both now and in future updates.

---

