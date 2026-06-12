---
title: "HELP - Mobility Radeon X600"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by IchigoKurosaki on 2006-11-04
Ok... First off I installed the ATI Drivers through APT-Get then I made the Ubuntu Packages from the latest drivers (8.3.30) and installed the packages through dpkg... and here I am now with no 3D Hardware Acceleration...

Here is my /etc/X11/xorg.conf
[QUOTE=/etc/X11/xorg.conf]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
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
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Mobility Radeon X600"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Mobility Radeon X600"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

#Section "Extensions"
#	Option	    "Composite" "0"
#EndSection[/QUOTE]

OK Before you say "Thats the problem" I know I have Composite commented out that is because when I uncomment it X11 Starts up and gives me a Black Screen of Doom... From what I have read "Option 'Composite' '0'" is suppose to give me 3D Hardware Acceleration and DRI, but it dosen't really work that well unless I want to play the Action packed game Black abyss... XD

Here is what i get with fglrxinfo...
[QUOTE=fglrxinfo]
root@laptop:~# fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
[/QUOTE]

and ofcource what I get with glxinfo | grep render
[QUOTE=glxinfo | grep render]
root@laptop:~# glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect
[/QUOTE]

This is the link that I followed to try and get it to work...
[Unofficial ATI Linux Driver Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

Thanks in advance for the help...

---

### Post by IchigoKurosaki on 2006-11-04
Ok don't worry I found the problem I typed [www.ubuntu.com](www.ubuntu.com) in and installed Kubuntu when I meant to type in [www.gentoo.org](www.gentoo.org) and install Gentoo... Everything is working now... emerge > APT... Thanks for nothing. :KS

---

