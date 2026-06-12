---
title: "Firefox with Edgy Eft - Choppy scrolling and slow refresh"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Surcouf on 2007-02-12
Just crossed over from the dark side and I'm loving it!
However, a little annoying thing seems to be bugging my browsing experience.
Firefox is behaving very strangely with my Edgy Eft new installation.  Scrolling is a pain in the %$& and is very slow and choppy.  It almost makes you seasick.  Enough to want to ditch it for another browser.  But I want to see if there is a solution first.

Here is my set-up:
ASUS M2NPV-VM
AMD Athlon 3200+ AM2
2 GB RAM
HD WD 250 SATA2
Integrated video nVidia GeForece 6150 + nForce 430

This is a new system with Ubuntu only.  Installation was done using CD install and went flawless ( so it seemed ) Can anyone help with this bugger.  Please keep in mind that I am a newbee.
Thanks

P.S. Did I mention I was a newbee?

---

### Post by confused57 on 2007-02-12
> **Surcouf said:**
> Just crossed over from the dark side and I'm loving it!
However, a little annoying thing seems to be bugging my browsing experience.
Firefox is behaving very strangely with my Edgy Eft new installation.  Scrolling is a pain in the %$& and is very slow and choppy.  It almost makes you seasick.  Enough to want to ditch it for another browser.  But I want to see if there is a solution first.

Here is my set-up:
ASUS M2NPV-VM
AMD Athlon 3200+ AM2
2 GB RAM
HD WD 250 SATA2
Integrated video nVidia GeForece 6150 + nForce 430

This is a new system with Ubuntu only.  Installation was done using CD install and went flawless ( so it seemed ) Can anyone help with this bugger.  Please keep in mind that I am a newbee.
Thanks

P.S. Did I mention I was a newbee?
Scrolling definitely shouldn't be choppy with your system.
Unless you've installed the "nvidia" drivers, you could check which driver Ubuntu selected for your video controller:
Open a terminal(Applications---Accessories---Terminal),enter:
```
cat /etc/X11/xorg.conf
```
scroll down to your video informations, make sure that "nv" is selected as the driver...if it's not, then:
backup your xorg first, by entering:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

then to edit:
```
gksudo gedit /etc/X11/xorg.conf
```
make necessary changes, then quit & save.

If you're using an LCD monitor, you probably already have your refresh rate at 60...if you're using a CRT, you might try reducing your refresh rate, it's worked for me, may or may not work for you.

You might also want to try out Swiftfox
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

I don't know if the protocol selected for your mouse would make a difference or not, I'm using a PS/2 & the protocol is  "ExplorerPS/2", which works for me.

It's probably something totally unrelated to what I've mentioned...

---

### Post by 454redhawk on 2007-02-12
I am also of the opinion that its the video driver.

---

### Post by trents on 2007-02-12
I have this same problem with a Radeon 9700 pro in Edgy but not in Dapper. Others have commented on this problem with Edgy but it is usually with Radeon video hardware. I hope someone comes up with a fix.

Steve

---

### Post by serag on 2007-02-12
if the browser scrolling is choppy, then your video driver is set to vesa. either set it to nv or install envy and use that to install the nvidia video drivers amd let it update your xorg.conf file

---

### Post by Surcouf on 2007-02-13
> **confused57 said:**
> Scrolling definitely shouldn't be choppy with your system.
Unless you've installed the "nvidia" drivers, you could check which driver Ubuntu selected for your video controller:
Open a terminal(Applications---Accessories---Terminal),enter:
```
cat /etc/X11/xorg.conf
```
scroll down to your video informations, make sure that "nv" is selected as the driver...if it's not, then:
backup your xorg first, by entering:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

then to edit:
```
gksudo gedit /etc/X11/xorg.conf
```
make necessary changes, then quit & save.

If you're using an LCD monitor, you probably already have your refresh rate at 60...if you're using a CRT, you might try reducing your refresh rate, it's worked for me, may or may not work for you.

You might also want to try out Swiftfox
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

I don't know if the protocol selected for your mouse would make a difference or not, I'm using a PS/2 & the protocol is  "ExplorerPS/2", which works for me.

It's probably something totally unrelated to what I've mentioned...

Thanks confused57!
Thanks to all those who responded so quickly!

That was it!!!
Setup was for 'vesa' type not nvidia.
I followed your instructions and solved the problem.
Thanks!  Much appreciated!
I'm definitely a convert now.
Surcouf

---

### Post by trents on 2007-02-13
Could this be the problem I've had with my Radeon card? Could it be set to VESA by default? Is there a ati or radeon setting to change to in xorg.conf?

I ditched Edgy because of this scrolling problem but here is the relevant section in my Dapper xorg.conf:

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
------------------------------------------------------------------------------------------------------------------
As you can see there the only references to the video card are "vesa" and "generic". Shouldn't there be some statement about ATI or Radeon? Note: I installed the fglrx drives from synaptic package manager already.

Steve

---

### Post by confused57 on 2007-02-13
Here's a tutorial that may help:
[http://www.ubuntuforums.org/showthread.php?t=32495&highlight=fglrx](http://www.ubuntuforums.org/showthread.php?t=32495&highlight=fglrx)

I think there are also generic drivers, "ati" & "radeon", also...but for optimum performance, flgrx is the best choice.

---

### Post by CalcProgrammer1 on 2007-02-13
Same problem here.  I mainly use Ubuntu on the live CD's now, cause my XP install is being stupid and every time I try to install ubuntu I end up killing my XP partition.  I've noticed that in 6.06 (Dapper), Firefox (which is version 1.5) scrolls smoothly, like in Windows.  However, 6.10 (Edgy) performance is overall, just bad.  I don't like the new boot screen and I definitely don't like the fact that it runs choppy on Firefox.  This COULD be related to the fact that edgy uses FireFox 2.0 rather than 1.5, but 2.0 for Windows XP runs great on the machine (AthlonXP 2600+,768MB RAM,ATi Radeon X1600Pro 512MB[AGP4X]).

---

### Post by vierdreieins on 2007-02-13
[QUOTE=serag]if the browser scrolling is choppy, then your video driver is set to vesa. either set it to nv or install envy and use that to install the nvidia video drivers amd let it update your xorg.conf file[/QUOTE]

This is probably my problem. Does anyone have an idea what driver I should use? I had it set to vesa, but I may have moved it when I was first fooling around with the configuration. (I was stupid and didn't back it up.) My video card is kind of crappy, and all I really know is that it's Intel Extreme Graphics.

---

### Post by MintabiePete on 2007-02-15
I had problems  with slow  scrolling in ubuntu 6.10 edgy  , ok on the bookmarks side but hell  on any page of firefox scrolling , I wasted a lot of time  trying  to improve my mouse  driver , but  It  wasnt until  I put Automatix2 on and  installed the  Nvidia  Drivers  to update my  Nvidia Geoforce 6100 onboard  video that it  came good . Now  my mouse scrolling is   perfect  :)

---

### Post by humbll on 2007-02-23
I am a Linux nOOb using a dell inspiron E1505 laptop with what I believe is an Intel 945GM Graphics Controller, what drivers do I pick for this? I had ubuntu edgy working fine, but i recently reinstalled and now i have choppy scrolling described in this thread. I did not do anything special the first time, it just worked automatically,](*,) ](*,) ](*,) ](*,) ](*,)  this time i installed, i used a script found in these forums fo installing edgy to encrypted filesystem. I know it is not the encryption doing it, it must be a driver problem. This is driving me nuts, please somebody help! Below is the contents of my xorg.config file:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-96
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by r4ik on 2007-02-23
Try,

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution)

Good luck !

---

