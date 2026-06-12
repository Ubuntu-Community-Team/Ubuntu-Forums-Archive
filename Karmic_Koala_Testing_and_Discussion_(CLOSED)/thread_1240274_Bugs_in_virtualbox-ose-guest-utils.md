---
title: "Bugs in virtualbox-ose-guest-utils"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-14
Is anyone here running Karmic in a VirtualBox guest. If you're using the OSE, there is a package in he repos that you can install in the guest instead of using VB's additions. The package is called virtualbox-ose-guest-utils. I have reported 2 bugs against this package:
[bug 411521]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/411521")
[bug 411518]("https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/411518")
Shared folders and shared clipboard work fine.
In Jaunty, the video worked and the mouse didn't. In Karmic, the mouse nearly works, and the video doesn't.

I think if this package was cleaned up, it would be easier to install than Guest Additions, and could be added to a Live CD.

---

### Post by vishalrao on 2009-08-14
i am using it... mouse integration works but video size is not working. will check out the bugs

edit: um, both bugs have the same number??? i marked them as "confirmed" is that appropriate?

---

### Post by phenest on 2009-08-14
> **vishalrao said:**
> edit: um, both bugs have the same number??? i marked them as "confirmed" is that appropriate?

Well spotted. I've changed the 2nd one.

---

### Post by phenest on 2009-08-14
Mandriva has this package as part of the Live CD. Nifty idea.

---

### Post by vishalrao on 2009-08-14
i get larger video if i paste the following into xorg.conf and restart kdm but the login screen is scrambled:

```
Section "Device"
     Identifier "Configured Video Device"
     Driver "vboxvideo"
EndSection
```

i will now try installing additions from the host - but yes - this should work from within the guest's packages...

---

### Post by phenest on 2009-08-14
> **vishalrao said:**
> i get larger video if i paste the following into xorg.conf and restart kdm but the login screen is scrambled:

```
Section "Device"
     Identifier "Configured Video Device"
     Driver "vboxvideo"
EndSection
```

i will now try installing additions from the host - but yes - this should work from within the guest's packages...

That's strange. I don't have a xorg.conf at all.

---

### Post by phenest on 2009-08-14
I made a new xorg.conf and used the vboxvideo driver. Not only do I have a larger video resolution, my mouse works correctly. Thanks vishalrao.

I wonder why my xorg.conf file was missing?

---

### Post by wayne_cat on 2009-08-14
> **phenest said:**
> I made a new xorg.conf and used the vboxvideo driver. Not only do I have a larger video resolution, my mouse works correctly. Thanks vishalrao.

I wonder why my xorg.conf file was missing?

Karmic's Xorg system probes the system to autoconfigure itself. A new Xorg feature.

---

### Post by phenest on 2009-08-14
> **wayne_cat said:**
> Karmic's Xorg system probes the system to autoconfigure itself. A new Xorg feature.

But why didn't the virtualbox-ose-guest-utils package configure it?

---

### Post by wayne_cat on 2009-08-14
> **phenest said:**
> But why didn't the virtualbox-ose-guest-utils package configure it?

good question ... could you please try this:

- stop Gnome and GDM ... it only works if Xorg is not running
- run this command to create a xorg.conf.new file 

```
sudo Xorg -configure
```Now have a look at the file ... is the option that vishalrao posted in the file?

---

### Post by phenest on 2009-08-14
Yep, that worked.
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
EndSection

Section "Module"
	Load  "record"
	Load  "dbe"
	Load  "dri2"
	Load  "extmod"
	Load  "glx"
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

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
	Identifier  "Card0"
	Driver      "vboxvideo"
	VendorName  "InnoTek Systemberatung GmbH"
	BoardName   "VirtualBox Graphics Adapter"
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

```

---

### Post by vishalrao on 2009-08-14
my bad, when i said i "pasted" the stuff into xorg.conf i also had to create the file first... the vbox guest utils didnt create it.

then i deleted the xorg.conf and installed the additions from the host vbox, this time it created the xorg.conf with just those 3 lines and i got larger screen but garbled KDM...

the kdm "garbling" was fixed by disabling 3d acceleration in the host vbox settings... now both the screen size and mouse pointer integration all fine for me too :)

do you have 3d compiz effects phenest?

---

### Post by wayne_cat on 2009-08-14
> **phenest said:**
> Yep, that worked.

maybe the the virtualbox-ose-guest-utils still use the function:

```
 dpkg-reconfigure xserver-xorg
```to configure Xorg after the installation ... this function does not work on Karmic any more (deprecated feature)

This "bug" is maybe something for VB forum. (VirtualBox is not a standard Ubuntu application)

---

### Post by phenest on 2009-08-14
> **wayne_cat said:**
> This "bug" is maybe something for VB forum. (VirtualBox is not a standard Ubuntu application)

I agree. I'll see if I can find anything over there.

---

### Post by vishalrao on 2009-08-14
Looks like the issue lies nearabouts the Xserver and it should be fixed soon enough as posted in the LP bug: see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540884](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540884)

---

### Post by wayne_cat on 2009-08-14
> **vishalrao said:**
> looks like the issue lies nearabouts the xserver and it should be fixed soon enough as posted in the lp bug: See [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540884](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540884)

+1

---

### Post by phenest on 2009-08-15
> **vishalrao said:**
> Looks like the issue lies nearabouts the Xserver and it should be fixed soon enough as posted in the LP bug: see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540884](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=540884)

Excellent!

---

### Post by phenest on 2009-10-06
I've done a fresh install of Karmic beta, but the guest utils don't appear to be working. I've used 'sudo Xorg -configure' to create a xorg.conf file, but there is no integration. Can anyone confirm?

---

