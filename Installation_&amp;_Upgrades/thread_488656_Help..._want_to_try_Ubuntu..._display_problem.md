---
title: "Help... want to try Ubuntu... display problem"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by jeremyrfoster on 2007-06-30
I'm trying to install Ubuntu on a Dell Latitude D600 on a Microsoft Virtual PC 2007 instance. It shows the initial install screen just fine, but when it gets into the desktop environment the resolution jumps to 1600x600 and I can barely see that the menu and desktop icons exist but it isn't usable. I tried the alternate install disk image... used the text install. With that I have to jack the resolution up really high so that the text menus (like country selection etc.) can be seen. Didn't get all the way through the install before it got stuck on a progress bar and didn't go any further. What's going on? Allocated 512MB to my VM. Mobility Radeon 9000 graphics card. 1400x1050 desktop. Thanks.
jf

---

### Post by Jose Catre-Vandis on 2007-06-30
Sugest the following

First off, can you see enough to try to change the screen resolution?

From the top menu panel:

System>Preferences>Screen Resolution

Make changes

Or try:

In the VM (once it has booted up), press
```
ALT+F2
```
then type:
```
gnome-terminal
```
In the terminal type:
```
sudo gedit /etc/X11/xorg.conf
```
this will ask for your password. Type it in, then a text editor should open up with your graphics card configuration file. Scroll down through the file unitl you get to the screen section. Change it to look like this:
```
Section "Screen"
	Identifier "Default Screen"
	Device     "#Leave the same as you find#"
	Monitor    "#Leave the same as you find#"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Save and exit from the text editor and reboot the VM.

Finally you can try to install the vm tools, but this will need to be done within the vm as it probably won't work if you try to install from the MSVPC menu.

As an alternate, why not create @ 8gb of space on your hard drive and install ubuntu there, you can then use all your native hardware

---

### Post by jeremyrfoster on 2007-06-30
Very helpful... I'll try. How do I install @8GB of my hdd... do I have to partition? Can I partition without messing up my main partition?
jf

---

### Post by weblordpepe on 2007-06-30
Just a quick note: alt-F2 and type **gnome-display-properties**
that will let you change your resolution.
Yes you can boot to either the Ubuntu live CD or the gparted live CD (AWESOME!) to fiddle with your partitions.
Its like partition magic, except free.

---

### Post by Jose Catre-Vandis on 2007-07-02
> **weblordpepe said:**
> Just a quick note: alt-F2 and type **gnome-display-properties**
that will let you change your resolution.
Yes you can boot to either the Ubuntu live CD or the gparted live CD (AWESOME!) to fiddle with your partitions.
Its like partition magic, except free.

Thanks weblordpepe (that's what i wanted to say but didn't know how!) :)

Where are all these command line commands posted?

---

### Post by weblordpepe on 2007-07-02
Umm next question :) I think the Ubuntu documentation might be a good place to look.

---

