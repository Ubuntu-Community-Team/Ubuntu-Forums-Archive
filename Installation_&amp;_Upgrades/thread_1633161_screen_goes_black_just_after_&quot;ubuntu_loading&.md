---
title: "screen goes black just after &quot;ubuntu loading&quot; icon appears for a couple of seconds"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by xihad76 on 2010-11-28
just installed fresh version of ubuntu 10.04 from live usb stick without experiencing any problem. while booting for the first time from new installation i got a black screen just after the "ubuntu loading" logo appears for a couple of seconds. the screen goes black . sometimes i can see the mouse cursor, sometimes not. nothing happens and it keeps doing like this. i searched for the solution and now think that this is an old graphics card issue. i have Esonic motherboard and AGP card is built in.  

need help badly. now running my pc from usb live stick as i have no other os installed right now. plz help.

---

### Post by xihad76 on 2010-11-29
ok. using lspci i got the info about graphics card:

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

please , help me out. :(

---

### Post by xihad76 on 2010-11-29
still struggling guys :( 
tried with nomodeset by editing grub.
tried to boot using failsafe graphics mode. but it said your input device and graphics card are not configured properly. configure it yourself.
i can boot using live usb without any problem as i m writing this comment from live usb boot. may b i need to configure my graphics card manually. 

plz help. switching back to xp is the last option i have in mind. but now seems like i have to .

---

### Post by xihad76 on 2010-11-30
well, i made it after trying various workouts for last 24 hours! 
in my case the life saver was newly created Xorg.conf file that is by default absent in ubuntu 10.04. 

firstly, i boot to recovery mode and run as root. ran the command " Xorg -configure" to auto create a xorg.conf.new file under /root and modified it according to my hardware specifications.then i placed it to /etc/X11 folder as xorg.conf 
my graphics card specification is: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03) and this was not configured automatically during installation. 


my modified xorg.conf is like this. 
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
	Load  "dbe"
	Load  "glx"
	Load  "record"
	Load  "dri"
	Load  "extmod"
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
	HorizSync     30-85
        VertRefresh   48-120
	VendorName   "Samsung"
	ModelName    "933SNPLUS"
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
	BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
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
		Modes  "800x600"
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
	Modes     "1024x768"
	EndSubSection
EndSection

```

hope this might help others with the same kind of problem. Cheers!

---

### Post by ENigma885 on 2010-12-05
xihad76, glad that u have overcome ur problem.

Do u have any Xorg ppa enabled?

---

