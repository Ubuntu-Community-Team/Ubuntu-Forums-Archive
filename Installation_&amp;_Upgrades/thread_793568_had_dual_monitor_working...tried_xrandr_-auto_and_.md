---
title: "had dual monitor working...tried xrandr -auto and lost it all"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Koohiisan on 2008-05-13
I have been a dual monitor XP user for years, and just recently decided to finally test the Ubuntu waters on my real hardware and not just a vm.  I selected Ubuntu Studio 8.04, and installed it without any problems.  The only issue I ran into was not having both monitors alive when the system was finished installing.

My video hardware consists of two separate cards: an AGP ATI All-In-Wonder 9700 Pro, and a dual-head ATI PCI 7000/VE card.  I have one monitor hooked up to the 9700, and a second monitor to one port of the 7000.

Initially, the first monitor was the only one that did *anything*.  After hours of reading online and playing around, I discovered 'X -configure', which actually detected my monitors properly!!  Success...kinda...

In XP, I was used to having one Windows session that spanned two monitors...here, I had two separate X sessions.  I guess I got greedy because I wanted the same single-session spanning both monitors in Ubuntu Studio.  I looked up Xinerama and tried to turn it on, but that did nothing for me.

Then...the killer...I ran 'xrandr -auto' just to see what it would detect and do...and now everything is nuts!  When grub boots me up, all the display including the Ubuntu Studio logo is on monitor one...THEN...when X starts, monitor one goes off and two comes on!  Even if I Ctrl-Alt-F1 to get to a command line monitor one is STILL off and never comes back even if I do an 'X -configure'!  >_<

I have tried 'dpkg-reconfigure xserver-xorg', and I think that actually worked for one whole session until I rebooted and it all went loony again.  I have replaced and reconfigured my xorg.conf a million times to no avail.  As a matter of fact, I had made backup copies with every change I made prior to the destruction of X, so I even tried one of those working ones!!  Nothing gives me back my two monitor system! ](*,)

So, I am wondering if xrandr stored it's setting somewhere other than xorg.conf, and it is sabotaging my efforts to get X back in line!  Could it be so?  How can I fix this?  Do I need to reinstall from scratch?

Thanks in advance!  Sorry for the long post, I thought explaining things might eliminate some early suggestions I've already tried.

---

### Post by Koohiisan on 2008-05-13
FWIW, here's my xorg.conf in its entirety:

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "extmod"
	Load  "GLcore"
	Load  "xtrap"
	Load  "glx"
	Load  "dbe"
	Load  "record"
	Load  "dri"
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
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "NoDRI"              	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "BusType"            	# [<str>]
        #Option     "DRM_nbufs"          	# <i>
        #Option     "DRM_bufsize"        	# <i>
        #Option     "Capabilities"       	# <i>
        #Option     "CapabilitiesEx"     	# <i>
        #Option     "ClientDriverName"   	# [<str>]
        #Option     "KernelModuleParm"   	# [<str>]
        #Option     "AGPMask"            	# <i>
        #Option     "AGPv3Mask"          	# <i>
        #Option     "BufferTiling"       	# [<bool>]
        #Option     "Profile"            	# <str>
        #Option     "RingSize"           	# <i>
        #Option     "EnableDepthMoves"   	# [<bool>]
        #Option     "GammaCorrectionI"   	# <i>
        #Option     "GammaCorrectionII"  	# <i>
        #Option     "OpenGLOverlay"      	# [<bool>]
        #Option     "DefaultVisualTrueColor" 	# [<bool>]
        #Option     "VideoOverlay"       	# [<bool>]
        #Option     "DesktopSetup"       	# [<str>]
        #Option     "MonitorLayout"      	# [<str>]
        #Option     "ForceMonitors"      	# [<str>]
        #Option     "EnableMonitor"      	# <str>
        #Option     "OverlayOnCRTC2"     	# [<bool>]
        #Option     "Mode2"              	# [<str>]
        #Option     "PairModes"          	# [<str>]
        #Option     "HSync2"             	# [<str>]
        #Option     "VRefresh2"          	# [<str>]
        #Option     "ScreenOverlap"      	# <i>
        #Option     "MemClock"           	# <i>
        #Option     "ASICClock"          	# <i>
        #Option     "UseInternalAGPGART" 	# [<bool>]
        #Option     "FastSwap"           	# [<bool>]
        #Option     "Stereo"             	# [<bool>]
        #Option     "StereoSyncEnable"   	# <i>
        #Option     "DisableOvScaler"    	# [<bool>]
        #Option     "UseFastTLS"         	# <i>
        #Option     "BlockSignalsOnLock" 	# [<bool>]
        #Option     "ForceGenericCPU"    	# [<bool>]
        #Option     "CenterMode"         	# [<bool>]
        #Option     "OffScreenPixmaps"   	# [<bool>]
        #Option     "EnableOpaqueOverlayVisual" 	# [<bool>]
        #Option     "TMDSCoherentMode"   	# [<bool>]
        #Option     "EnablePrivateBackZ" 	# [<bool>]
        #Option     "TVFormat"           	# [<str>]
        #Option     "TVStandard"         	# [<str>]
        #Option     "TVOverscan"         	# [<bool>]
        #Option     "TVHSizeAdj"         	# <i>
        #Option     "TVVSizeAdj"         	# <i>
        #Option     "TVHPosAdj"          	# <i>
        #Option     "TVVPosAdj"          	# <i>
        #Option     "TVHStartAdj"        	# <i>
        #Option     "TVColorAdj"         	# <i>
        #Option     "PseudoColorVisuals" 	# [<bool>]
        #Option     "PreferredVRefresh"  	# <i>
        #Option     "FastStart"          	# [<bool>]
        #Option     "ProfileDriver"      	# [<bool>]
        #Option     "PPPTforGART"        	# [<bool>]
        #Option     "TexturedVideo"      	# [<bool>]
        #Option     "TexturedVideoSync"  	# [<bool>]
        #Option     "Textured2D"         	# [<bool>]
        #Option     "TexturedXrender"    	# [<bool>]
        #Option     "DPMS"               	# [<bool>]
        #Option     "MaxGARTSize"        	# <i>
        #Option     "LogoPosX"           	# <i>
        #Option     "LogoPosY"           	# <i>
        #Option     "LogoColFG"          	# <i>
        #Option     "LogoColBG"          	# <i>
        #Option     "SwapScreens"        	# [<bool>]
        #Option     "FBC"                	# [<bool>]
        #Option     "FrontBufferMode"    	# <i>
        #Option     "BackBufferMode"     	# <i>
        #Option     "DepthBufferMode"    	# <i>
        #Option     "OverlayBufferMode"  	# <i>
        #Option     "VideoOverlayBufferMode" 	# <i>
        #Option     "EnableIrqMgr"       	# [<bool>]
        #Option     "EnableMulticard"    	# [<bool>]
        #Option     "EnablePPLIB"        	# [<bool>]
        #Option     "DefaultOnDC"        	# [<bool>]
	Identifier  "Card0"
	Driver      "fglrx"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon R300 ND [Radeon 9700 Pro]"
	BusID       "PCI:1:5:0"
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
        #Option     "DDCMode"            	# [<bool>]
        #Option     "IgnoreEDID"         	# [<bool>]
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
        #Option     "DynamicClocks"      	# [<bool>]
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
	Identifier  "Card1"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon RV100 QY [Radeon 7000/VE]"
	BusID       "PCI:2:6:0"
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

---

### Post by Koohiisan on 2008-05-16
Any ideas?

Do I just have to reinstall to get it working again?

:(:(:(:(:(

---

