---
title: "Lower resolution in 7.10 but xorg.conf looks OK"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by pwrcul on 2007-11-23
I would like to run Ubuntu 7.10 using my Nokia 445Xi monitor and my Nvidia 6600 based video card at 1280x1024@85Hz.

The only refresh choices I have now are 50 and 54Hz at 1280x1024.  If I reduce the resolution, there are more options.

I have been exploring Ubuntu gradually over more than a year while still wedded to Win XP because of work.  The two OSs are in a dual boot system.

After reading a bunch of previous posts on lower resolution after upgrading, I could not see where what I have in xorg.conf should not work.  The horizontal and vertical refresh are now the same as in the Nokia 445Xi documentation.  I only tweaked the upper limit of the default "Vertrefresh 50-120" so it conforms to Nokia documention of 50-150.  Here are the relevant sections:
Section "Device"
	Identifier	"NVIDIA GeForce 6600"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Videoram	256000
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Nokia 445Xi"
	Option		"DPMS"
	Horizsync	30-102
	Vertrefresh	50-120           <--- This should be 50-150 so I changed it to 150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6600"
	Monitor		"Nokia 445Xi"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1600x1200"	"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

I then checked Xorg.0.log  I marked some descrepancies with "<--" in the right margin, but I don't see why they would prevent a broader and higher choice of refresh rates.  Here are the sections I believe are relevant:
[parts up to here deleted]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 (NV43) at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.16.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:5:0:0:
(--) NVIDIA(0):     Nokia (CRT-0)
(--) NVIDIA(0): Nokia (CRT-0): 400.0 MHz maximum pixel clock  <-- Nokia docs say >= 200MHz
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1600x1200"; removing.    <-- Nokia says can do @ 75Hz
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (83, 89); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

[parts deleted]

(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX

[parts deleted]

(II) NVIDIA(0): Setting mode "1280x1024_60"  <-- not sure what this means, but looks like trouble
[end of file]

The one other factor I can think of is that I run the monitor through a KVM switch.

Someone thought creating Modelines would help in another situation.  For the sake of completeness here are two modelines I generated with [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) that I found with Google:
Modeline "1472x1104@75" 200.00 1472 1504 2256 2288 1104 1125 1139 1160
Modeline "1280x1024@88" 200.00 1280 1312 2064 2096 1024 1042 1057 1076
I did not stick them in yet.

Thanks in advance.

---

### Post by pwrcul on 2007-11-24
Update.  I added a Modeline to xorg.conf and generated trouble:

Section "Monitor"
     Identifier "Nokia 445Xi"
     Option "DPMS"
     Horizsync 30-102
     Vertrefresh 50-150
     Modeline "1280x1024@85" 188.40 1280 1312 2024 2056 1024 1043 1057 1076  
EndSection

That disabled the System-->Preference-->Screen Resolution.  It gave the spinning wheel and disappeared.
Fortunately I had a terminal window already opened and copied back the prior version of xorg.conf

It also disabled the GreenRunningPerson-->Shut Down option.  You get other options, but not Shut Down.
It also disabled Applications-->Accessories-->Terminal  so I could not open a terminal window again.

So I googled and found I could Ctrl-Alt-F2 (or 1-6 since X uses 7) and get a text entry access requiring my login and password.
There I entered shutdown -r now
On rebooting I could access Screen Resoution at 50 and 54HZ.

So just the modeline is not sufficient.

---

### Post by pwrcul on 2007-11-24
Update:  
I modified the modeline so it has the same first part as the Screen section, i.e., "1280x1024" as in

Section "Monitor"
	Identifier	"Nokia 445Xi"
	Option		"DPMS"
	Horizsync	30-102
	Vertrefresh	50-150
        Modeline "1280x1024" 188.40 1280 1312 2024 2056 1024 1043 1057 1076
EndSection

That caused easily as much trouble as the last version.  I am baffled.  

If anyone has solved this kind of problem, I would like to know what worked.

---

### Post by pwrcul on 2007-11-25
Some improvement:

I returned to do another run of what I last did but follow up by checking Xorg.0.log as a way of perhaps getting some hints.
Instead of using sudo xinit -- :2 which before gave a lot of trouble I used
    sudo /etc/init.d/gdm start
and that seemed to make a big difference.  I don't know why.  I had no trouble to recover from.
Also I put in another Modeline to see what messages pushing for even higher resolution would provoke as follows:

Section "Monitor"
Identifier "Nokia 445Xi"
Option "DPMS"
Horizsync 30-102
Vertrefresh 50-150
Modeline "1600x1200" 245.66 1600 1632 2560 2592 1200 1223 1238 1261
Modeline "1280x1024" 188.40 1280 1312 2024 2056 1024 1043 1057 1076
EndSection

To my amazement the higher, "1600x1200", resolution was accepted for the first time, and I got three refresh rates for 1280x1024:  51, 64, 65.
The failures of terminal, shut down, etc. did not crop up.  
Below are relevant sections of Xorg.0.log.  Note that it reports "Unable to get display device CRT-0's EDID"
So, it looks like I will need to bypass that--and learn more about it.
My trial and error is getting me somewhere.
If anyone has a clearer understanding and advice, I would love to have a clearer path to eventually getting higher horizontal refresh, like 85Hz.

[first parts deleted]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 (NV43) at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.16.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:5:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
[part deleted]
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
[part deleted]
(II) NVIDIA(0): Setting mode "1280x1024"
(II) NVIDIA(0): Setting mode "1280x1024_60"

---

