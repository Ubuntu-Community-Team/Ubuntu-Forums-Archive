---
title: "Dual Monitors in seperate sessions"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lachild on 2009-03-17
Am I the only one that uses dual monitors configured for separate sessions?  If not, is anyone else seeing the issues with the second session?

Seems this option has been broken since Ibex which is why I decided to beta test so it didn't happen again on this release, but am  I the only one who uses this and if so can some one tell me the best way to set up X with dual monitors with monitors that use different resolutions?


Thanks
LaChild

---

### Post by Blue Beard on 2009-03-17
I am using xrandr to setup the second monitor.
$ xrandr --output DVI-I_2/analog --mode 1280x1024
$ xrandr --output DVI-I_2/analog --right-of VGA_1

xrandr --help will list the options


The key part of xorg.conf for me:

Section "Device"
	Identifier	"HD3450"
	Driver		"radeonhd"
        Option    	"monitor-VGA_1" "Daytek LCD TV"
        Option    	"monitor-DVI-I_2/analog" "Daytek 17 inch CRT"
	Option		"DRI" "on"
EndSection

Section "Monitor"
	Identifier	"Daytek LCD TV"
EndSection

Section "Monitor"
	Identifier	"Daytek 17 inch CRT"
	VendorName	"Daytek"
	ModelName	"G701PF"
	HorizSync	30-72
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Left"
	Monitor		"Daytek LCD TV"
	Device		"HD3450"
	DefaultDepth	24
	SubSection	"Display"
	    Depth	24
	    Modes	"1024x768"
	    Virtual	2704 1050
	EndSubSection
EndSection

---

### Post by RAOF on 2009-03-17
> **lachild said:**
> Am I the only one that uses dual monitors configured for separate sessions?  If not, is anyone else seeing the issues with the second session?

Seems this option has been broken since Ibex which is why I decided to beta test so it didn't happen again on this release, but am  I the only one who uses this and if so can some one tell me the best way to set up X with dual monitors with monitors that use different resolutions?
...

You seem to be asking two different questions here.  Do you want two different sessions (KDE + GNOME simultaneously, for example)?  This is much more difficult - it'll require starting 2 separate XDM instances, two X servers, etc.

Simply having each monitor running at a different resolution is *easy*.  System->Preferences->Screen Resolution (in GNOME) will have both your monitors shown, and you can independently change their resolution.  KDE has a similar tool, but it didn't seem to actually work last time I tried it :).  

If you're using a proprietary driver, you'll need to use their configuration tool instead - that's nvidia-settings for the nvidia driver, and some other thing for fglrx.

---

### Post by hockeyhead019 on 2009-03-17
that seems mind blowing to have both a gnome session and a kde session running... not sure y anybody would wanna do that but still seems cool haha

---

### Post by LordVeovis on 2009-03-17
Actually you really sparked my interest there... How in the world would you setup a gnome / kde session simultaneously?  I know you can have sepparate x sessions open, but can you map one to a whole separate monitor?  If so, could you please explain how this is done because I would like t do that!!

---

### Post by caryb on 2009-03-18
Running Gnome & KDE simultaneously would take bug reporting to whole new level:lolflag:


Cary

---

### Post by lachild on 2009-03-18
> **Blue Beard said:**
> I am using xrandr to setup the second monitor.

Thanks I'll look into that.  


> **RAOF said:**
> You seem to be asking two different questions here.  Do you want two different sessions (KDE + GNOME simultaneously, for example)?  This is much more difficult - it'll require starting 2 separate XDM instances, two X servers, etc.

Not surprising... I woke up this morning and had hoped that this post had just gone into the void.  One thing I learned was never post the day after an all nighter.  lol.

What I was really tring to find out was is the percentage of people using separate X screens was too small to put these issues on the radar and if so what is a better way to do this.  Looks like I got both questions answered last night.  The bugs that I've been experiencing were present in Gnome 2.24 and a bug was already reported so I was able to look into this.


> **RAOF said:**
> 
Simply having each monitor running at a different resolution is *easy*.  System->Preferences->Screen Resolution (in GNOME) will have both your monitors shown, and you can independently change their resolution. If you're using a proprietary driver, you'll need to use their configuration tool instead - that's nvidia-settings for the nvidia driver, and some other thing for fglrx. 

That's true but that causes the smaller monitor whole screen to scroll up and down and side to side (unless I set this up wrong).  After awhile you get pretty dizzy. lol


> **RAOF said:**
> 
Do you want two different sessions (KDE + GNOME simultaneously, for example)?

Wow I never thought of that...  That would be pretty cool but not very practical.  Still it might be a fun project to attempt sometime.


Thanks for the responses everyone.


LaChild

---

### Post by lachild on 2009-03-18
> **lachild said:**
> 
That's true but that causes the smaller monitor whole screen to scroll up and down and side to side (unless I set this up wrong).  After awhile you get pretty dizzy. lol

Well now don't I feel silly.  I just switched to twin view and this doesn't seem to be a problem anymore.

Doh!:oops:

---

