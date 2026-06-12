---
title: "Screen resolution problem:"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by plantboy1 on 2008-08-25
I recently did a clean reinstall of Ubuntu on one of my systems, an old, windows 95 era gateway.  It's a pentium 3, two hard drives, and it's using a Mag Innovision DX17F monitor.

The first time I had Ubuntu on that system, it ran at a resolution of about 1268x800 or something (high resolution widescreen thing).  Since I've reinstalled I reconfigured everything to the way I'd had it before, not too hard since Ubuntu has all the drivers for the monitor and the graphics card.  The Xorg config file says that Ubuntu can use high resolutions, but no matter what I do (I've tried several different drivers, just out of curiousity) it will not use a resolution of above 800x600.

Can anyone help me?

---

### Post by kagashe on 2008-08-27
I had to read your other posts and now assume that earlier you did distribution upgrade from Ubuntu 7.10 to 8.04 on this machine and now you have done a clean install and not getting the resolution of 1268x800 now (and it was available on upgraded 8.04).

You said that you reconfigured everything as before (I assume before means on Ubuntu 7.10). By this I assume that you copied the xorg.conf used in Ubuntu 7.10 in Ubuntu 8.04 and it is not working.

I suggest the following.
1.0 Back up your existing xorg.conf
> $ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
2.0 Delete your existing xorg.conf
> $ sudo rm /etc/X11/xorg.conf
3.0 Reboot.

Don't be afraid Ubuntu 8.04 does not need any xorg.conf.

See what resolution you get.

kagashe

---

### Post by Millerthomson on 2008-08-27
I installed ubuntu on my system for windows 98 which has a pentium 4 processor, but i cant get the high resolution wide screen. Please somebody help me!

=================================================================

Miller Thomson

[Louisiana Alcohol Addiction Treatment]("http://www.alcoholaddiction.org/louisiana")

---

### Post by kagashe on 2008-08-27
> **Millerthomson said:**
> I installed ubuntu on my system for windows 98 which has a pentium 4 processor, but i cant get the high resolution wide screen. Please somebody help me!

=================================================================

Miller Thomson

[Louisiana Alcohol Addiction Treatment]("http://www.alcoholaddiction.org/louisiana")
Please open a terminal and type the following commands and post the output here.
> $ lspci | grep VGA
$ xrandr -q

Please post the Device section of /etc/X11/xorg.conf file.

kagashe

---

### Post by kagashe on 2008-08-27
@ plantboy1
If you are scared of deleting xorg.conf and trying you can see what is available in your present setup through this command:
> $ xrandr -q

and set up through
> $ xrandr --output VGA/VGA-0 --mode 1268x800

If 1268x800 is shown as available by xrandr -q
Use VGA or VGA-0 as shown by xrandr -q

kagashe

---

### Post by plantboy1 on 2008-08-27
> **kagashe said:**
> @ plantboy1
If you are scared of deleting xorg.conf and trying you can see what is available in your present setup through this command:


and set up through

If 1268x800 is shown as available by xrandr -q
Use VGA or VGA-0 as shown by xrandr -q

kagashe

I tried that, first the thing in the terminal, which said the maximum I could use was 824x624, and that I was already using it.  From there, it just went down to lower resolutions.  

Also, deleting the xorg.conf file didn't do anything for me.

---

### Post by kagashe on 2008-08-27
> **plantboy1 said:**
> Also, deleting the xorg.conf file didn't do anything for me.When you delete xorg.conf, xorg tries to detect your graphic card and monitor as best as it can and loads the driver it thinks ok and selects a resolution for you. When you said it "didn't do anything for me" I assume that it could not do better than 824x624. Same as what you could do by writing xorg.conf yourself. Please correct me if I am wrong in my assumptions because some people get flickering or blank screen after deleting xorg.conf.

> which said the maximum I could use was 824x624, and that I was already using it. From there, it just went down to lower resolutions.
Could you please try this after deleting xorg.conf also and post the output of xrandr -q here.

In addition please attach the file /var/log/Xorg.0.log to your post.

> The first time I had Ubuntu on that system, it ran at a resolution of about 1268x800 or something (high resolution widescreen thing).
Do you have the values of horizontal synchronization and vertical refresh rate for your monitor?

kagashe

---

### Post by bitra on 2008-08-28
The first time I install Ubuntu 8.04, the screen resolution set to 800x600. There's no option for 1024x768 or above on "Screen Resolution" menu.

After searching for answers and failed, I'm pretty sure this is what works for me:

[LIST=1]
[*]Go to System > Preferences > Main Menu

[*]On the left side (Menus), click "Other". You can see on the right side (Items), there's "Screens and Graphics". If the checklist is still uncheck (as the default), check it so it will appear on you main menu.

[*]After it appear on your main menu, click it (where a popup window of Screen and Graphic Preferences will appear).

[*]Set you monitor model and screen resolution. Be sure to click Test to make sure the setting is o.k.

[*]After you finish put the required setting, reboot your machine.

[*]That's it. (I hope) your Ubuntu will display at the desired screen resolution.
[/LIST]

Here's the sample of my xorg.conf file:

```

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce4 (generic)"
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP Pavilion M45/S40 Monitor"
	Horizsync	31.468-50.0
	Vertrefresh	56.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

My Ubuntu 8.04 now displaying at 1024x768 resolution! Hell yeah!

I hope this information could be useful for you. :)

---

