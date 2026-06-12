---
title: "Hardy + nVidia legacy = no display!"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by ygarl on 2008-02-15
Hello all,

Just upgraded on a sad whim to Hardy and found I was defaulting to a admittedly much nicer graphics mode than the old "blue screen of X" I am used to when the nVidia drivers aren't working.
I should mention here: I'm not a newbie in this respect, so the command line is good for me if you have advice requiring Bash. I'm no guru, but typing commands suits me fine...

I tried going through the menu, and selecting the proprietary driver just defaulted back to the nv driver.
I tried changing the driver manually on the xorg.conf like I used to: no dice. Back to the nv driver again and the nice menu, no glx.

I went down to Gnome to check out the Restricted Drivers menu... and it simply wasn't there! It is completely missing!
What happened there then?

I went to synaptic and completely uninstalled the nvidia-glx package which I was using before, then reinstalled it after rebooting.

No glx again (glxgears fail, etc.)...
Strange...
Uninstalled nvidia-glx completely, and installed the legacy package (surprised the standard one worked before anyways - I have an old Geforce 2 card.).
No glx... Set the xorg.conf 

I don't really want to start tracking down nVidia's drivers from the website, changing inittab etc. if I can help it.

1) Where is the Restricted Drivers control panel item? Anyone know how I can even reinstall it?
2) What's with the drivers? The new menu, apt-get and synaptic both fail to install the glx drivers (at least and have them working...)

Confused...

---

### Post by agharbeia on 2008-05-05
> **ygarl said:**
> 
1) Where is the Restricted Drivers control panel item? Anyone know how I can even reinstall it?
2) What's with the drivers? The new menu, apt-get and synaptic both fail to install the glx drivers (at least and have them working...)


The "Rrestricted drivers" control applet is now called "Hardware drivers".

I'm still having problems with nvidia-glx-legacy, though.

My nVidia is recognised and appears as "in use" in the applet, but I cannot change the resolution to anything more than 800x600.

The upgrade to Hardy has wrecked many things in my system, however xorg.conf was intact as it were, but still, the display  and serial mouse aren't working as they did.

---

### Post by EnkiduinNZ on 2008-05-07
> **agharbeia said:**
> The "Rrestricted drivers" control applet is now called "Hardware drivers".

I'm still having problems with nvidia-glx-legacy, though.

My nVidia is recognised and appears as "in use" in the applet, but I cannot change the resolution to anything more than 800x600.

The upgrade to Hardy has wrecked many things in my system, however xorg.conf was intact as it were, but still, the display  and serial mouse aren't working as they did.

For some reason Ubuntu seems to use xorg.conf.failsafe. I gave up in the end and used Envy ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)), but you need to uninstall this every time you upgrade the drivers.

Cheers,

Cliff

---

### Post by agharbeia on 2008-05-07
EnvyNG didn't work for me.
What worked eventually was using the "nv" driver instead of "nvidia".
The mouse problem was solved simultaneously also by that!
However, with no acceleration, graphics-intensive applications like GoogleEarth and SecondLife do not work. I haven't tested graphics editing softwares extensively yet (GIMP, Inkscape), but I expect degradation in speed.

lspci -nn returns:
```

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15)

```

I have to say however that this is all using kernel 2.6.22-14, as the kernel which ships with hard (2.6.24.16) has another bug which prevents me from using it altogether. So I guess it will be infeasible to report this rare configuration now (rather old kernel and legacy nVidia), at least until I'm able to use the latest kernel sometime in the future.

---

### Post by nemarona on 2008-05-11
Just to show some support: EnvyNG didn't work for me either (nor did any of the many suggestions I found in the forums). There seems to be a problem with Hardy and the legacy nvidia drivers, for I remember they used to work with earlier Ubuntu versions.

My setting:
```
$ lspci -n | grep 0300
01:00.0 0300: 10de:002d (rev 15)

$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
```

---

### Post by L_V on 2008-05-21
nvidia-legacy installation to summarize:

	_Mandriva_: easy / immediate / nothing to do
	_Debian_: installing the nvidia.run from nvidia site works fine; just xorg.conf to tweak to get openGL
	_Ubuntu Gutsy/Hardy_: seems impossible.

May be ubuntu should cooperate with Debian or mandriva to investigate.

---

### Post by russnash37 on 2008-07-08
I noticed that there seem to be quite a few threads like this, both here and on other forums, reference getting nvidia working with Hardy.  I just upgraded my sons computer from Gutsy to Hardy and was having issues, his machine has an Nvidia Riva TNT2 64.  I finally got 3D support working so thought I should post my findings somewhere so that it will hopefully help others:

On Gutsy, I simply activated the restricted driver in Restricted Drivers manager, however, after upgrading to Hardy the new Hardware Drivers app did not offer a proprietary driver.  Here's what I did:


```
sudo apt-get install nvidia-glx-legacy
sudo apt-get install nvidia-legacy-kernel-source nvidia-settings
```

I then reverted /etc/X11/xorg.conf to the following from the working Gutsy install:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"NoLogo"	"True"
	Option		"AllowGLXWithComposite"	"True"
EndSection

Section "Monitor"    *** WARNING!!  See the note below! ***
	Identifier	"Sylvania"
	Option		"DPMS"
	Option		"HorizSync"	"30-70"  <- Change these to match
	Option		"VertRefresh"	"50-90"  <- your monitor!
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
	Monitor		"Sylvania"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1152x864"	"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

PLEASE NOTE!!!  The monitor section includes settings and refresh rates for my sons monitor!  You *MUST* substitute these for your monitors own settings, simply copying the above *MAY* damage your monitor!

I rebooted the system and 3D worked fine.

The above xorg.conf is rather 'dirty' in my opinion and could be cleaned up a bit, but works nonetheless.

Hopefully, this will help someone out.

Russ.

---

