---
title: "how do I set screen to 1680 x 1050?"
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by hill0093 on 2007-02-23
How do I set screen to 1680 x 1050? It doesn't do this itself at installation, and I cannot find a place to do it.

---

### Post by taurus on 2007-02-23
You need to install a driver for your graphic first before you can go to a higher resolution.  What kind of video card do you have on your machine anyway?

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by hill0093 on 2007-02-23
I found that it knows the monitor is 1680x1050, but the monitor doesn't know that the computer knows si it keeps blinking to tell operator to set it.

---

### Post by taurus on 2007-02-23
Have you installed a driver for your graphic card?  It doesn't matter what you have set in /etc/X11/xorg.conf.  It will not go any higher until you install a driver for your graphic card.

---

### Post by hill0093 on 2007-02-23
Card is Albatron nVIDIA GeForce FX5200 Video Card, 128MB DDR, 64-bit, DVI/TV-Out, 8X AGP, Model "FX5200EP".
I don't have internet connected. I suppose I have to do that first.

---

### Post by taurus on 2007-02-23
Yes, get your network working first since you need to install nVidia driver for your card because you are using nv right now and as far as I know, nv can't go any higher than 1024x768.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by douglerner on 2007-03-02
I found the following at another forums, but it didn't work. After doing the specified settings my 1680x1050 resolution still doesn't show up.

This is on a MacBook Pro 17". The installed video card appears to be a RadeonX1600.

These are the instructions I followed that didn't work:

First, open up a terminal. From there, type the following:

sudo gedit /etc/X11/xorg.conf

You might need to enter an admin's password here. You should be presented with a text window with a bunch of stuff. Ignore most of it, but look for the following:

Modes "1024x768" "800x600" "640x480"

It'll appear several times throughout the file. Each time you see it, add your desired resolution (in your case, 1680x1050) so that it appears like the following:

Modes "1680x1050" "1024x768" "800x600" "640x480"

(You can also add any other resolutions you'd like Ubuntu to support.) From there, shut down Ubuntu and, under your VM settings in Parallels, add the same resolutions you previously added to Xorg.conf (Don't forget to tick the box that says "Enable custom screen resolutions"). Then just reboot Ubuntu and your new resolutions should be available!

---

### Post by xx6xx on 2007-12-17
> **douglerner said:**
> 
...
First, open up a terminal. From there, type the following:

sudo gedit /etc/X11/xorg.conf

You might need to enter an admin's password here. You should be presented with a text window with a bunch of stuff. Ignore most of it, but look for the following:

Modes "1024x768" "800x600" "640x480"

[SIZE="6"]It'll appear several times throughout the file[/SIZE]

What if it doesn't ? I have the same problem, but in my xorg.conf there is no "Modes ... " 
Should I add it ? If yes... where? In which sections... ?

THX for Answer

---

### Post by rsarvi on 2008-03-25
^^^

I have the same problem as above person.

I dont have Modes under display. No "Subsection" parameters for that display. Do I need to add it? 

I know that my graphic card will support 1680x1050, since i have set my windows with that resolution

pls advice

its urgent

---

### Post by hill0093 on 2008-04-13
When I 
 ls -l /etc
I get
drwxr-xr-x 10 root root      4096 2008-02-23 01:00 X11
Then when I 
ls -l /etc/x11
I get
ls: /etc/x11: No such file or directory
even if I use sudo

WHY???

---

### Post by warp99 on 2008-04-13
> **rsarvi said:**
> ^^^

I have the same problem as above person.

I dont have Modes under display. No "Subsection" parameters for that display. Do I need to add it? 

I know that my graphic card will support 1680x1050, since i have set my windows with that resolution

pls advice

its urgent
Sure go ahead and add the section in bold so it looks similar to this:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV43 [GeForce 6200]"
        Monitor         "monitor1"
        Defaultdepth    24
        [b]SubSection "Display"
                Depth      24
                Modes    "1680x1050"
        EndSubSection[/b]
EndSection
```

Or you can just do the following:

```
sudo dpkg-reconfigure xserver-xorg
```

then don't use the autodetect, choose 'nv' or whatever your driver is for your card, then when you get to the monitor section choose '1680x1050' as your highest resolution. When completed just crtl+alt+backspace to reload xserver.

---

### Post by warp99 on 2008-04-13
> **taurus said:**
> Yes, get your network working first since you need to install nVidia driver for your card because you are using nv right now and as far as I know, nv can't go any higher than 1024x768.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

Sure it can, I run '1680x1050' on the nv driver all of the time when I have problems with CompizFusion. Just change 'nvidia' to 'nv' in xorg.conf and restart xserver. If the card and the monitor can run the resolution it will run, no problems.

---

### Post by ryanhaigh on 2008-04-13
The FX5200 may have problems with 1680x1050 over dvi (at least the model I used to have did), I had to do some research but eventually found a page that had xorg.conf options you could use to enable this resolution over dvi. This isn't the page I used but may be useful: [http://www.nvnews.net/vbulletin/showthread.php?t=88154](http://www.nvnews.net/vbulletin/showthread.php?t=88154)
The same info is also given here: [http://dotcommie.net/dc.php?page=blog.php&from=5](http://dotcommie.net/dc.php?page=blog.php&from=5)

---

### Post by warp99 on 2008-04-13
> **ryanhaigh said:**
> The FX5200 may have problems with 1680x1050 over dvi (at least the model I used to have did), I had to do some research but eventually found a page that had xorg.conf options you could use to enable this resolution over dvi. This isn't the page I used but may be useful: [http://www.nvnews.net/vbulletin/showthread.php?t=88154](http://www.nvnews.net/vbulletin/showthread.php?t=88154)
The same info is also given here: [http://dotcommie.net/dc.php?page=blog.php&from=5](http://dotcommie.net/dc.php?page=blog.php&from=5)

If you need a modline entry in your xorg.conf open a terminal and issue the following:

```
cvt 1680 1050
```
you get an output similar to this:
```
# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync

```
then add the modeline to your monitor sections:
```
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0
        [b]modeline        "1680x1050_60.00" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0[/b]
EndSection
```
then the resolution to your screen section:
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6200]"
	Monitor		"monitor1"
	Defaultdepth	24
	[b]SubSection "Display"
		Depth	24
		Modes "1680x1050_60.00"
	EndSubSection[/b]
EndSection
```
The changes are printed in bold.

---

