---
title: "fix for ati video drivers on upgrade to edgy"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by cogenthack on 2006-10-27
i had a little trouble with the upgrade in the form of:
```
(==) Log file "/var/log/Xorg.0.log"
(==) using config file : "/etc/x11/xorg.conf"
(EE) failed to load module "ati" (module does not exist,0)
(EE) no drivers available
```
either it was something I did during the install (via the update manager) or the drivers don't come pre-configured. I did this:
started up in "recovery mode" and then typed:
```
sudo aptitude install xserver-xorg-video-ati
```
perhaps it will generalise to similar problems.

---

### Post by firestorm1080 on 2006-10-27
Thanks! You saved my day! :D

---

### Post by yelloguy on 2006-10-27
I had the same problem yesterday and posted a similar solution.

---

### Post by magog96 on 2006-10-27
> **cogenthack said:**
> 
I did this:
started up in "recovery mode" and then typed:
```
sudo aptitude install xserver-xorg-video-ati
```
perhaps it will generalise to similar problems.

I did a new installation yesterday and the hint above didn't help. I also removed and installed xserver-xorg again.

I've got an ATI X850 XT PE (PCIE)

My Xorg.0.log:
```
(II) Primary Device is: PCI 01:00:0
(II) ATI:   Candidate "Device" section "ATI Technologies, Inc. R480 [Radeon X850$]
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found

```

I also checked /etc/X11/xorg.conf:
```
Section "Device"
      Identifier    "ATI Technologies, Inc. R480 [Radeon X850XT Platinum...]"
      Driver        "ati"
      BusID         "PCI:1:0:0"
EndSection
```


Finally I tried the "fglrx" driver...and this worked! :D 
```

1. Boot in recovery mode
2. sudo aptitude install xorg-driver-fglrx
3. manually edit /etc/X11/xorg.conf to use the "fglrx" driver instead of the default "ati" (see below)
4. reboot
```

I added some '#' to the old Section "Device" and the Device line at the "Screen" section to have a backup.

Now the xorg.conf looks like this:
```

#Section "Device"
#	Identifier	"ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Graphics Adapter 0"
	Driver		"fglrx"
	Option		"UseInternalAGPGart" "no"
	#Option		"KernelModuleParm" "agplock=0"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay"	"off"
	#Option		"DesktopSetup"	"clone"
	BusID		"PCI:1:0:0"
EndSection


Section "Monitor"
	Identifier	"L365"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
#	Device		"ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
	Device		"ATI Graphics Adapter 0"
	Monitor		"L365"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

I only need to configurate my DualHead setup as I have two EIZO L365 on my desk!

[EDIT]
Because of the missing kernel module the above solution is not yet working accelerated, but at least you have a working X.

Now I'm installing eComStation 1.2R on another partition (and this will work out of the box).

cu

---

### Post by magog96 on 2006-10-27
> Because of the missing kernel module the above solution is not yet working accelerated, but at least you have a working X.


Ok, it's now also on the KnowIssues list with workarounds included.
See this page: [https://wiki.ubuntu.com/EdgyKnownIssues](https://wiki.ubuntu.com/EdgyKnownIssues)

Bugs are:
[http://launchpad.net/bugs/28925](http://launchpad.net/bugs/28925)
[http://launchpad.net/bugs/57716](http://launchpad.net/bugs/57716)

---

### Post by Roobert on 2006-10-27
I'm having the same problem of no devices being found with a broken xserver.

I tried the suggestion of switching my driver name in xorg.conf from ati to radeon, and is still doesn't work. I've installed all drivers with ```
sudo apt-get install xserver-xorg-video-all
``` so that can't be the problem. I've also tried the vesa and fglrx drivers to no avail. 

Using the ATI 300X driver. 

~ R.

---

### Post by bugz0r on 2006-10-27
How do I edit xorg.conf? I try sudo gedit /etc/X11/xorg.conf but it doesn't work.

---

### Post by magog96 on 2006-10-27
Hi!

> **Roobert said:**
> I'm having the same problem of no devices being found with a broken xserver.
[..]
Using the ATI 300X driver. 


I'm still trying to get an accelerated X but beside that it worked for me (even the change from "ati" to "radeon" did work).

What does "/var/log/Xorg.0.log" say?

---

### Post by ZagiFlyer on 2006-10-27
> **bugz0r said:**
> How do I edit xorg.conf? I try sudo gedit /etc/X11/xorg.conf but it doesn't work.

If your xserver isn't starting, then you can't use gedit (because it's an X/Gnome application). You'll need to use a text editor like vim, nano or emacs. If you've never used any of these, I would recommend nano or vim.

---

### Post by Roobert on 2006-10-31
> I'm still trying to get an accelerated X but beside that it worked for me (even the change from "ati" to "radeon" did work).

What does "/var/log/Xorg.0.log" say?

My Xorg.0.log is *really * long, so I'll paste in pieces that seem to be troublesome. 

I notice that I have a section that says:

```
LoadModule: "kbd"
Warning, couldn't open module kbd
UnloadModule: "kbd"
Failed to load module "kbd" (module does not exist, 0)
LoadModule: "mouse"
Warning, couldn't open module mouse
UnloadModule: "mouse"
Failed to load module "mouse" (module does not exist, 0)
```

My device:
```
Primary device is : PCI 01:00:0
```

Another error further along:

```
fglrx: No matching Device section  for instance (BusID PCI:1:0:1) found
```

I'm not sure what I should be reporting here....at the very end of the log, there are lots of errors about:

```
Error opening /dev/wacom
No such file or directory
```



And finally, the last error that I can see in the log is:

```
Fatal server error:
failed to initialize core devices
```

Can anyone help me?

---

### Post by h2gofast on 2006-11-05
Quote:
Originally Posted by cogenthack View Post
I did this:
started up in "recovery mode" and then typed:
Code:

sudo aptitude install xserver-xorg-video-ati

perhaps it will generalise to similar problems.
I did a new installation yesterday and the hint above didn't help. I also removed and installed xserver-xorg again.



I was running a dual monitor setup with an nvidia agp card and an ati pci card.  
Upgrading to edgy the ati card wouldn't work.

sudo aptitude install xserver-xorg-video-ati

fixed it in a pinch.    :-D

---

### Post by jgcamp99 on 2006-11-06
> **magog96 said:**
> I did a new installation yesterday and the hint above didn't help. I also removed and installed xserver-xorg again.

I've got an ATI X850 XT PE (PCIE)

My Xorg.0.log:
```
(II) Primary Device is: PCI 01:00:0
(II) ATI:   Candidate "Device" section "ATI Technologies, Inc. R480 [Radeon X850$]
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

Fatal server error:
no screens found

```

I also checked /etc/X11/xorg.conf:
```
Section "Device"
      Identifier    "ATI Technologies, Inc. R480 [Radeon X850XT Platinum...]"
      Driver        "ati"
      BusID         "PCI:1:0:0"
EndSection
```


Finally I tried the "fglrx" driver...and this worked! :D 
```

1. Boot in recovery mode
2. sudo aptitude install xorg-driver-fglrx
3. manually edit /etc/X11/xorg.conf to use the "fglrx" driver instead of the default "ati" (see below)
4. reboot
```

I added some '#' to the old Section "Device" and the Device line at the "Screen" section to have a backup.

Now the xorg.conf looks like this:
```

#Section "Device"
#	Identifier	"ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
#	Driver		"ati"
#	BusID		"PCI:1:0:0"
#EndSection

Section "Device"
	Identifier	"ATI Graphics Adapter 0"
	Driver		"fglrx"
	Option		"UseInternalAGPGart" "no"
	#Option		"KernelModuleParm" "agplock=0"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay"	"off"
	#Option		"DesktopSetup"	"clone"
	BusID		"PCI:1:0:0"
EndSection


Section "Monitor"
	Identifier	"L365"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
#	Device		"ATI Technologies, Inc. R480 [Radeon X850XT Platinum (PCIE)]"
	Device		"ATI Graphics Adapter 0"
	Monitor		"L365"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

```

I only need to configurate my DualHead setup as I have two EIZO L365 on my desk!

[EDIT]
Because of the missing kernel module the above solution is not yet working accelerated, but at least you have a working X.

Now I'm installing eComStation 1.2R on another partition (and this will work out of the box).

cu

I had an issue yesterday w/ Edgy where my desktop would freeze, it turned out I had to change the opengloverlay to "on", it was set to "off". I'm kinda surprised yours even boot into a desktop other than root on the first time. Those were my symptoms.

---

### Post by jgcamp99 on 2006-11-06
> **bugz0r said:**
> How do I edit xorg.conf? I try sudo gedit /etc/X11/xorg.conf but it doesn't work.

You don't need to do that, use the text editor in your applications menu drop down. Edit the text in the file like you would a word document and save it.

---

### Post by jgcamp99 on 2006-11-06
BTW, there's a wiki that explains some of this, but you have to read thru a couple of different methods to understand what they're talking about for each section and apply it to what you want to do.

[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

and this one has a lot more things covered for installing Ubuntu applications and features.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28ATI.29)

This is a gold mine of information.

---

