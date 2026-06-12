---
title: "Can't get 6.10 installed on inspiron 4000"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by hupjack on 2007-02-11
So I installed XP, on an unformatted totally fresh HD.  Partitioned the drive leaving 10GB for the ubuntu installation that I was going to install next.

attempting to boot from the ubuntu disk, after the initial ubuntu boot menu, choosing option 1 to boot the live cd or install ubuntu, I then spend some time with the ubuntu logo up there, and a progress bar-ish thing going back n forth.

then that goes away and I end up with a flashing underscore
I don't imagine there is anything magic to type, since keyboard input doesn't post to screen.

nothing else notable happens, accept that the fan comes on..  clearly the CPU is being taxed... not sure by what though..    you can't here it accessing the HD or CD

any ideas?  I really wanted to dual boot and finally try out a linux distro..  I heard this was the place to start

---

### Post by meng on 2007-02-11
1. Check the md5sum of the iso you burned from.
2. Consider reburning the CD at lower speed
3. Consider downloading and burning the Alternate CD instead of the Live Desktop one.

---

### Post by hupjack on 2007-02-11
one other weird thing..  

seemed like it was choking on the display..  as in video card stuff.
this dell has some mobo integrated ATI card.

when I went back to XP, it threw up a BSOD saying some part of the ATI driver was stuck in an infinite loop.. 

I also noticed, even while trying to boot up XP before the BSOD, it had shrunk the XP logo down..  the thing was trying to use a chunk of the monitor that was a smaller inner 10" square I'd guestimate rather than the full 15"  When it booted in safe mode, it still only used that smaller inner square.   Then I downloaded some 2003 dell / ati drivers off the dell site (not sure which ones I'd use from ATI directly)  doesn't look like they have a package that supports these integrated deals.

anywho after installing the ati / dell "updated" video drivers, the thing booted backup without a bsod and used the entire screen this time..

seems like while the ubuntu install was choking trying to deal with this ati integrated Piece of #$#@, maybe it set something on the card, that the window ati driver then further choked on?

or maybe it's not a driver issue at all and that video card is done for..  seems to be holding together fine now though after updating the xp / dell / ati graphics driver

---

### Post by hupjack on 2007-02-11
So.  I reburned the live cd at 8 or 12x I think it was..  and still no dice..

why do you suggest the "alternate CD"?  A different startup routine might get around my little issue?  Other people with this laptop seem to be doing ok
[http://ubuntuforums.org/showthread.php?t=359020](http://ubuntuforums.org/showthread.php?t=359020)

---

### Post by meng on 2007-02-11
There are boot options from the Live CD such as safe graphics mode, noacpi, noapic, nolapic; invoke as many of these as you can. Ultimately, though, you may need the Alternate CD.

---

### Post by luisito on 2007-02-19
I am typing this reply with my Dell Inspiron 4000 running Kubuntu Edgy. Everything worked to me pretty much out of the box. I have to say however, that I never did a fresh install of Edgy. I updated from Dapper from then net instead. A fresh install should be even better.

With your description, I find it difficult to understand what is going on. It sounds like you didn't get anything to work. If you press Ctrl-Alt-F1 does it switch to the first console? If it does, then the problem might be that xorg was not set up well and that would be easy to solve copying my configuration. If it does not, then we have to think about something else (and I can't think of anything now).

If Ctrl-Alt-F1 does switch to the console, then you should get a login screen (in text mode). You can login there and type 
[INDENT]sudo nano /etc/X11/xorg.conf[/INDENT]
which would open the configuration file of X after asking for your password. The important part is the device section. Scroll down till you find it. The safest choice would be to change the value of Driver to "vesa". It should look something like this:

Section "Device"
        Identifier      "ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

That would most likely make xorg work. Press Ctrl-X to close nano and save the file. Then type startx and pray.

If everything goes well that should get X to work. I guess that would make you happy at the beginning, but then you would realize it is a bit slow. That is not because the computer is five years old, but more because you need to set up the right driver. The Dell Inspiron 400 has an ATI mobility 128 (or at least mine does). My xorg.conf is copied below, which works well for me. Maybe it is not enough to run Beryl, but at least it will show all the OpenGL screensavers nicely.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Rage Mobility M3 AGP 2x"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

