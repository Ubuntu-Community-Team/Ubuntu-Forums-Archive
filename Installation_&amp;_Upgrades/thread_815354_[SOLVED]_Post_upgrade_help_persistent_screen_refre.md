---
title: "[SOLVED] Post upgrade help: persistent screen refresh settings"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by mazirian on 2008-06-01
I finally got around to upgrading to hardy this weekend and after the upgrade I can no longer maintain the refresh rate I want xorg to use.  I want a 1600x1200@75 mode. Though I tinker and tinker with my xorg.conf, and I am able to set the correct refresh rate using nvidia-settings (but not the useless gnome utility), I am completely unable to find a way to keep that mode through a restart of the xserver.  In other words, I have to reset the fresh rate to 75 each time I log in to gnome by using nvidia-settings.

Any ideas on how to force the refresh rate to 75?

Here is my current xorg.conf:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonicP810-3"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 180.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5900XT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1200_75 +0+0; nvidia-auto-select +0+0; 1600x1200 +0+0"
    SubSection     "Display"
        Depth       24
		#Modes		"1600x1200@75"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"
    EndSubSection
EndSection


```

---

### Post by hal8000 on 2008-06-01
Couple of things for you to try:
First install xresprobe xrandr  (if they're not already installed)

xrespobe will tell you what reolution your monitor supports:

sudo xresprobe any

will print the list. Now see what current resolution you're using:

xrandr -q

You'll get a list, similar to mine below:

anc@orac:~$ xrandr -q
Screen 0: minimum 320 x 240, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0*    51.0  
   1280x960       52.0  
   1280x800       53.0  
   1280x768       54.0  
--snip--

The asterisk indicates current mode. For me it states 1280x1024 @50Hz,
however my OSD on my monitor tells me I'm at 60Hz vertical and 63.9KHz horizontal: this is correct for my monitor. 
The settings on your OSD of your monitor will be correct, but now to generate your desired resolution try:

xrandr -s 1600x1200 -r 75

This will work as a normal user and should change your resolution and refresh rate, however check settings with your monitor OSD.
If all goes well, you can set this my making an entry in
/etc/rc.local

add the line
xrandr -s 1600x1200 -r 75

just above exit 0.

Make sure you've not disabled rc.local from rc.conf or sysv-conf-rc and reboot.

An alternative method may be to run
sudo dpkg--reconfigure xserver-xorg

The latest Xorg is capable of running without xorg.conf, I believe it now probes your monitor and graphics card automatically, there have been numerous posts about this on the Debian forums.
If xrandr works, then there should be no reason to obtain your refresh rate this way.
Hope that helps.

---

### Post by mazirian on 2008-06-01
Thanks, that is pretty instructive.  I've not had this difficulty with X before.  Indeed, there is a big variance between what the OSD says I'm running at (H 93.7, V 75 -- which is what I want) and what xrandr reports ( which is "1600x1200 50.0*").

But, if I run ...

```
xrandr -s 1600x1200 -r 75
```

I get ...

```
Rate 75.0 Hz not available for this size
```

..when clearly it is.  Oddly, the nvidia-settings utility does report an accurate range of frequencies to choose from.

Anyway, these are the utilities I needed, so I'll keep tinkering.

---

### Post by hal8000 on 2008-06-02
> **mazirian said:**
> Thanks, that is pretty instructive.  I've not had this difficulty with X before.  Indeed, there is a big variance between what the OSD says I'm running at (H 93.7, V 75 -- which is what I want) and what xrandr reports ( which is "1600x1200 50.0*").

But, if I run ...

```
xrandr -s 1600x1200 -r 75
```

I get ...

```
Rate 75.0 Hz not available for this size
```

..when clearly it is.  Oddly, the nvidia-settings utility does report an accurate range of frequencies to choose from.

Anyway, these are the utilities I needed, so I'll keep tinkering.


Ignore what xrandr states, your monitor OSD graphics will be correct, just make sure the Horizontal and Vertical rates are within the limits that your monitor can display.

Also found
grandr  (provides a GTK interface to xrandr) and displayconfig, though
not tried these yet.

[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

There was a post about krandr displaying different refresh rates to what the monitor uses (and I cant remember which forum, think it was PCLinuxOS).
In any case, if you were at 50Hz on a CRT you would see flicker, LCD displays, offer lower refresh rates but the flicker is less of a problem.

---

### Post by mazirian on 2008-06-02
Well I'm happy to ignore xrandr, except that the command does nothing since it thinks that the refresh rate is impossible.  In other words, it is impossible to set the correct refresh rate with xrandr.

  I think the answer may have something to do with turning of the option that tells xorg to use edid.  I'll test that next

---

### Post by mazirian on 2008-06-02
So the issue was that I needed to include 

```
Option "UseEDIDFreqs" "False"
```

in my xorg.conf, remove the metamodes line and then insert a modes line.

My new screens section is as follows:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEDIDFreqs" "False"
    Option         "TwinView" "0"
    #Option         "metamodes" "1600x1200_75 +0+0; nvidia-auto-select +0+0; 1600x1200 +0+0"
    SubSection     "Display"
        Depth       24
	Modes       "1600x1200_75" "1280x1024_75" "1024x768_75" "800x600_75" "640x480_75"
    EndSubSection
EndSection

```

---

