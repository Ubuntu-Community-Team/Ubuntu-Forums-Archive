---
title: "After Upgrade to 12.04, amdcccle not functional"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by cturnes on 2012-09-17
Hi all,

I hope I'm posting this in the right area.  I upgraded to 12.04 from 10.04 this morning, and after solving a slew of other upgrade problems, I've been unable to get my dual monitor set up properly working.  Back on 10.04, I had my two monitors successfully configured for multiple desktops, with resolutions of 1440x900 and 1920x1080, respectively.

After upgrading, the monitor configuration wouldn't allow me to change from mirror mode.  The same thing happened on 10.04, so I took the normal steps.  First, I tried to install the ATI/AMD proprietary FGLRX graphics driver from the "Additional Drivers" menu in System Settings.  The installation failed, so I followed the steps for a terminal-based installation, which appears to have succeeded.

After rebooting, etc., I ran amdcccle as sudo.  Whenever I get the monitor setup that I want, though, nothing happens when I hit "apply."  It tells me that it's been reconfigured and that I should reboot, but the monitor setup is absolutely no different.  

I looked around for what might be causing this, but I didn't find anyone with exactly the same problem.  It's not that amdcccle is crashing for me, and the problem isn't necessarily that the settings aren't persistent, it's just that it seems incapable of actually modifying any of the settings, even in administrative mode.

I tried the regular monitor configuration again, but it gives me the error of the size/position of the monitors exceeding the limit.  I've tried browsing various forums, but none of the proposed solutions seem to work.

Here's the output of fglrxinfo:
> 
root@ct5254aa-01:~# fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon HD 3450
OpenGL version string: 3.3.11627 Compatibility Profile Context

and here's the relevant portion of my xorg.conf:
> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
	HorizSync    31.0 - 70.0
	VertRefresh  40.0 - 75.0
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
	HorizSync    31.0 - 70.0
	VertRefresh  40.0 - 75.0
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"

	#	Driver		"fglrx"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	DefaultDepth     24
	SubSection "Display"
		Virtual   3360 1920
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection


The display for the Default Screen has the right dimensions for what I want to do, so I'm not sure why the Display Manager yells at me when I try to increase the resolution.  Any ideas?

UPDATE:  After modifying the amdcccle screen in the xorg.conf file, I seem to be able to achieve the resolution I want.  Oops...

> 
Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
                Virtual   3360 1920
		Depth     24
	EndSubSection
EndSection


---

