---
title: "Beryl not working/Firefox very slow after upgrade"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by prosonik on 2007-04-21
Update;

Everything is working! After scouring the forums, somebody on a different thread suggested to reconfigure xserver. I first made sure all packages were installed and up to date:
 ```
apt-get update
``` 
After running apt, the update manager said the upgrade was not finished. It installed about 5 packages. I did not note which ones. 

Second, I ran:

```
sudo dpkg-reconfigure xserver-xorg
```

To finish, I restarted x using ```
ALT-CTL-BACKSPACE
``` When x restarted, everything seemed to running 100%; allot snappier then Edgy. I was able to turn on Compiz with no issues. I have not tested Beryl. Reflecting, I'm wondering if there was not an existing  issue with my edgy install. 

Hope this helps someone.

Prosonik

---


Hi All,
Upgraded last night using the software-update path. Everything was straight forward. However, after finishing this morning, i booted black screen.. Rebooted again and was able to get back into gnome.. Turned on beryl, and gnome-session crashed. I launched into fail-self xterm, and tried firefox.. It was terribly slow I used automatrix to install opera, and was able to get a browser back up. I then manually launched gnome-session and was able to turn off beryl, and remove it from the start-up.
After that, I was able to get into the system, and everything seemed fine. 


Except: 
1.firefox is still unusable. 
2. Beryl crashes every time it launches.. I've tested all the other apps i use,  and it seems to be working. 
i believe that it's something to do with the video card driver, but I'm not sure where to go next. 
Here is my current xorg.
```


Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection




Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "dbe"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

#Section "Monitor"
#	Identifier   "aticonfig-Monitor[0]"
#	Option	    "VendorName" "ATI Proprietary Driver"
#	Option	    "ModelName" "Generic Autodetecting Monitor"
#	Option	    "DPMS" "true"
#EndSection



Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        #HorizSync       28-72
        #VertRefresh     43-60
EndSection


Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
	Option          "AGPMode"       "4"
        Option          "AccelMethod"   "EXA"
        Option          "ColorTiling"   "on"
	Option "AGPMode" "4"
	Option "DisableGLXRootClipping" "true"
	Option "AddARGBGLXVisuals" "true"
	Option "AllowGLXWithComposite" "true"
	Option "XAANoOffscreenPixmaps" "true"
	Option "EnablePageFlip" "true"
	Option "DRI" "true"	
	Option "AccelMethod" "EXA"
	Option "EXANoOffscreenPixmaps"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "RenderAccel" "true"
EndSection



#Section "Device"
#	Identifier  "aticonfig-Device[0]"
#	Driver      "ati"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
#EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                #View Port 0 0
		Modes           "1440x900" "1024x768"
        EndSubSection
EndSection




#Section "Screen"
#	Identifier "aticonfig-Screen[0]"
#	Device     "aticonfig-Device[0]"
#	Monitor    "aticonfig-Monitor[0]"
#	DefaultDepth     24
#	SubSection "Display"
#		Viewport   0 0
#		Depth     24
#	EndSubSection
#EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

and the output of
```
$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```


Ideas? Suggestions? thanks!

---

