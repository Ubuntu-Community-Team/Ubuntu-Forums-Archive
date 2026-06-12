---
title: "[SOLVED] xorg.conf not populated after install"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by L84DNR on 2008-07-02
Hello, 

I installed Ubuntu 8.0.4 desktop on my Pentium4 system.  Everything seemed to go fine until post install I tried to change the resolution level.  I found the GUI to be grayed out.  

I found that the **/etc/X11/xorg.conf** file to only contain the following simple information (Below).

Doing a "**lshw**" shows my video card-sorry I didn't capture model yet.  I think it was intel.  I ran all updates but still nothing.  I am currently re-installing to see if I missed anything.

Any suggestions?  Thanks, Jay:guitar:


more /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
etc...
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "pc105"
Option "XkbOptions" "none"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"

---

### Post by avtolle on 2008-07-02
[https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) will give you a general overview of how xorg now works in 8.04 (and, from reading, in other "new"releases of other distros).

On resolution, try```
gksudo displayconfig-gtk
```to choose your monitor (if listed); you can also click on the graphics card tab to see whether the system is detecting your card, and if not, if listed, you can select it also. Good luck.

---

### Post by L84DNR on 2008-07-02
Thank you.  It looks like I have a little reading to do. 

I will report back when I try, got tied up for the rest of the day.

Thanks!

---

### Post by L84DNR on 2008-07-05
I tried "gksudo displayconfig-gtk" but it won't launch.  Probably the same reason, Preference > Screen Resolution menus are grayed out.  I did some reading and that command launches the "Advanced" feature of that tab  (see output below)

I read the [link]("https://help.ubuntu.com/community/XORGHardy") 
provided and it sounds like I need to find the proper driver to use with my video card.  I understand the simplified xorg file and the dynamic recognition at startup.  I would still like to over-ride this and see if I can get higher resolution more out of my video card.

I use 'sudo lshw' to find my video card is " 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device " 

I know this isn't a great video card but it is what I have with this system and I would still like to be able to have gui or xorg config to control resolution.  I am new to using Ubuntu so not sure if I should just start trying one or both of these drivers in my xorg file?  Is there a command to reload-reinitialize the xorg file once I make these changes?

Driver      "Intel"
Driver      "i810"

Thank you again for the support.  As I mentioned, I am new to Ubuntu but my goal is to make this my main workstation.  I have a technology job routing,switch,voice but have only basic linux knowledge.  Jay


kuhne@jk:~$    gksudo displayconfig-gtk
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 404, in _finalizeInit
    gfxcard._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1123, in _finalizeInit
    screen._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1588, in _finalizeInit
    (cw,ch,x,x) = self.x_live_screen.getSize()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 77, in getSize
    return self.sizes[self.currentsizeid]
IndexError: list index out of range
jkuhne@jk-redhat:~$ sudo displayconfig-gtk
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 404, in _finalizeInit
    gfxcard._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1123, in _finalizeInit
    screen._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1588, in _finalizeInit
    (cw,ch,x,x) = self.x_live_screen.getSize()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 77, in getSize
    return self.sizes[self.currentsizeid]
IndexError: list index out of range
jkuhne@jk-redhat:~$ bullet-pro

---

### Post by avtolle on 2008-07-05
I'd try the "Intel" option first. However, reading the messages makes me wonder if the monitor horizontal and vertical refresh rates are being correctly detected, which would make it necessary to edit the file to include the correct rates in it. Do you have this information?

---

### Post by avtolle on 2008-07-05
In reading some other threads, it seems that the "old fix" which doesn't work for everyone will work for some. In a terminal```
sudo dpkg-reconfigure -phigh xserver-xorg
``` followed by a reboot. Give it a try.

---

### Post by L84DNR on 2008-07-05
Thank you again for the replies.  It's a dell monitor that's at least 5-6 years old. I don't have the model# of know the refresh rate.  Although, I can find out.  Monitor and the box are at work.   To you point, maybe I should try another newer monitor, reboot and see what happens.

Will also try the 'intel' driver in x-org and the command you mentioned. I tried something similar last week, (sudo dpkg-reconfigure xserver-xorg) but it only took me through the keyboard portion of install and then exited.

Thanks again, I will reply but will probably be Monday.  Have a great weekend!:popcorn:

---

### Post by avtolle on 2008-07-05
Have a good weekend, too. 

Why I was wondering about the monitor specs; it may be necessary to manually edit the /etc/X11/xorg.conf file to set up the monitor there, and I didn't want you to fry the monitor. I hold little hope for the sudo dpkg-reconfigure -phigh xserver-xorg command under 8.04, but have seen a few threads where the poster states that it worked. Good luck.

---

### Post by L84DNR on 2008-07-05
Thanks.  I'm not worried about the monitor but I can lookup the model number and specs so we can try setting from xorg.conf.  I'll get another monitor if I fry it...we have many of these older ones. Can't used the new ones without a new vid card as they are DVI. Will let you know.

---

### Post by L84DNR on 2008-07-08
Hi,

I have an update.  I was able to switch to a newer flat panel monitor (HP 2035) with a VGA port.  

My windows PC on the same monitor seems to have pretty decent resolution look feel(Divers are loaded) at 1400 x 1050

I tried to run ```
 sudo dpkg-reconfigure -phigh xserver-xorg 
``` but it just re-created the same file.  I did a diff with the backup and no changes.  Thanks for the suggestion though.

So I went for what you reccomended and updated the driver to use "Intel"

After doing 'man intel' it said my card was supported.  (845G)

I restarted the system and it came up fine but still the GUI menu System > Preferences > Screen resolution are grayed out.  

Now I'm looking to see if I can edit the xorg.conf again for resolution and refresh rate.  Just need to figure out the correct format.  I used the same monitor on my windows PC (with drivers installed) and it looks good at 1400 x 1050 with 75Hertz refresh.

Do you know any quick pointers to the format for this?  I have googled but seems there are different ways to specify. (Also different version of Ubuntu and Nvidia vs. Intel cards).

The 'man intel' didn't have how to do this with its options.

So in summary I'm in the same boat but now running the intel driver for my video card. 

Thanks again for your help.

---

### Post by avtolle on 2008-07-08
Try this again```
gksudo displayconfig-gtk
```and see if the HP monitor is listed and if so, select it to see whether we can get the resolution set correctly. If this doesn't work, then we'll need to go to manually editing the /etc/X11/xorg.conf file.

---

### Post by peterroots on 2008-07-08
when I first tried Kubuntu8.04 the screen on my laptop was all but unreadable .  On my fist attempt i gave up and went back to 7.10.  I did find 8.04 worked fine in a virutalbox so I recently gave it another try.
Same problem with an unreadable screen which I finally found was due to an almost empty xorg.conf file - rebuilding it automatically (as someone suggested in this post as well) did not make any changes.  fortunately I had a backup with my old file so I just copied the 7.10 version straight over and everything worked fine after that and I was then able to get the nvidia driver to install and work (had been fine in 7.10)
Based on my experience how about trying an older version, maybe as a liveCD and making a copy of the xorg.conf file to use in case this picks up the relevant settings?  It may save you having to build the file yourself.

---

### Post by L84DNR on 2008-07-08
> **avtolle said:**
> Try this again```
gksudo displayconfig-gtk
```and see if the HP monitor is listed and if so, select it to see whether we can get the resolution set correctly. If this doesn't work, then we'll need to go to manually editing the /etc/X11/xorg.conf file.

Yeah!  It worked, I was able to select my model and device and supported resolutions came up fine.  Only thing now is that I am stuck in a meeting so VNC access did not come back after restart.  Can't wait to get back to my desk to see.  Thank you so much!!

By the way, here is a related post that was interesting: [http://ubuntuforums.org/showthread.php?t=808812](http://ubuntuforums.org/showthread.php?t=808812)

---

### Post by L84DNR on 2008-07-08
> **peterroots said:**
> when I first tried Kubuntu8.04 the screen on my laptop was all but unreadable .  On my fist attempt i gave up and went back to 7.10.  I did find 8.04 worked fine in a virutalbox so I recently gave it another try.
Same problem with an unreadable screen which I finally found was due to an almost empty xorg.conf file - rebuilding it automatically (as someone suggested in this post as well) did not make any changes.  fortunately I had a backup with my old file so I just copied the 7.10 version straight over and everything worked fine after that and I was then able to get the nvidia driver to install and work (had been fine in 7.10)
Based on my experience how about trying an older version, maybe as a liveCD and making a copy of the xorg.conf file to use in case this picks up the relevant settings?  It may save you having to build the file yourself.
peterroots - Thanks for sharing your expierence.  That would be a good idea with a live CD to get the xorg.conf off a 7.1 system.  Hardware doesn't change makes sense this would carry forward.  I am new to Ubuntu so didn't realize the 8.0.4 version had the whole dynamic xorg situation.  

Luckily for me, spawning the GUI worked from the command line in this case when the gui would not: gksudo displayconfig-gtk   

Still waiting to get out of this meeting and back to my desk so I can see what was written in the xorg.conf

---

### Post by L84DNR on 2008-07-08
It looks pretty good.  I would like to see higher resolution 1600x1200@75, but only seems to be able to support that resolution at 65hz.  It seems like it just goes down the list of supported settings in the xorg.conf and picks the first one it sees that it will support. 

I tried modifying the file and only putting two or three to force 1600x1200@75 hertz but it wouldn't take. 

But overall, problem solved.  Thanks again for your help.  For reference, the second of my xorg.conf file now looks like this

[HTML]Section "Device"
	Identifier	"Card0"
	Boardname	"intel-mobile-video"
	Driver		"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "screen1" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 845"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1400x1050@75"	"1600x1200@65"	"1400x1050@60"	"1600x1200@60"	"1280x960@75"	"1600x1200@75"	"1280x1
024@60"	"1600x1200@70"	"1280x1024@85"	"1792x1344@60"	"1280x960@85"	"1856x1392@60"	"1280x960@60"	"1920x1440@60"	"1280x1024@75""1152x864@75"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x60
0@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Hewlett-Packard"
	Modelname	"HP L2035 Flat Panel Monitor"
	Horizsync	30.0-94.0
	Vertrefresh	48.0-85.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
[/HTML]

---

### Post by avtolle on 2008-07-08
Glad it worked. Would you be so kind as to mark the thread solved, using the thread tools at the top (I don't recall if to the left or to the right) so others can save a bit of time? Thanks (and glad you were able to survive the meeting).

---

### Post by L84DNR on 2008-07-08
Done thanks again!

---

