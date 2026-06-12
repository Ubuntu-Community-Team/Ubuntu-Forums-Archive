---
title: "Please Help! (Ubuntu Installation Problem)"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by raveneffct on 2006-12-06
I am new to Linux and have only windows xp running on my computer. I have downloaded and burnt Ubuntu onto a cd, when I go to install it..the ubuntu screen comes up and I click install...it installs but then a screen comes up telling me that the **x server** cannot work and there is a problem with my **graphical interface**. 

I know this is a common problem but I have looked EVERYWHERE for 5 hours straight, on multiple message boards and I can't seem to get it to work! And I have used the search...but the codes I enter do not work.

I read there are commands to enter...but the only command prompt I get is after 2 error messages that say yes to diagnose the problem and no..once I go through both of those it goes to a black command prompt with nothing written. I try to enter the codes people have suggested, when I hit enter nothing happens.

Please help I would REALLY appreciate it, I did use this cd on one of my older computers and it worked perfectly. I really want Linux on my machine!

Dell Dimension DM051
Intel Pentium 4 cpu 3.00ghz
512mb RAM
ATI Radeon X300 128mb Hypermemory

---

### Post by Sef on 2006-12-06
Could you please give some information about the computer: ram, processor, graphics card, etc.

---

### Post by raveneffct on 2006-12-06
> **Sef said:**
> Could you please give some information about the computer: ram, processor, graphics card, etc.

Dell Dimension DM051
Intel Pentium 4 cpu 3.00ghz
512mb RAM
ATI Radeon X300 128mb Hypermemory

---

### Post by Sef on 2006-12-06
Are you using the Live CD or the alternate cd?  If you are using the Live CD to install, I would recommend trying the alternate cd.   It has worked at times where the Live CD has failed.

---

### Post by raveneffct on 2006-12-06
Yes I am using the live install, Has the alternate version been known to bypass the X-Server error?

Also, what Alternate version should I download..and what is the difference?

---

### Post by canvasman on 2006-12-06
Don't know if this will help, but i had the same problem with the live cd 2 times..mmm..I set the bios to boot only from the cd and shut off the hard drive option till after it was loaded. I also had a problem with a HP dvd drive that stopped it.:confused:

---

### Post by raveneffct on 2006-12-06
Also, does the alternate cd allow you to duel boot as well?

---

### Post by renzokuken on 2006-12-06
yes

---

### Post by raveneffct on 2006-12-06
I used the alternate cd and the same exact thing happens! ARGH! I see the Ubuntu logo and loading bar...then once that finishes a screen comes up telling me something about an X-Server problem/Graphical Interface is not working.

Someone...please, help me :( I'm desperate at this point..I've been doing this for 6+ hours and still nothing!

---

### Post by Sef on 2006-12-06
I suspect that there is an incompatibility with a piece of your hardware (likely the graphics card.)  I really can't tell you more what to do to get Ubuntu up and running.  I hope someone with some more knowledge comes up with something that works for you.

Sometimes the only thing to do is use another distro.  For example, there was an old computer at work that I could only install with Vector Linux, which is based on slackware.  Any other type of distro (debian, redhat, etc.) would not work.

---

### Post by raveneffct on 2006-12-06
Is there any kind of codes I could put in the GRUB command line or edit mode. (now that the alternate cd has installed grub)

---

### Post by Sef on 2006-12-06
What do you want to do exactly?

---

### Post by styfer on 2006-12-06
hi i may refer u to this thread

[http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ati+x800](http://www.ubuntuforums.org/showthread.php?t=190133&highlight=ati+x800)

---

### Post by Malac on 2006-12-06
Boot into (recovery mode) from GRUB menu then type :
```
dpkg-reconfigure xserver-xorg
```at the prompt.
Try choosing a lower resolution 1024x768 or 800x600 and see if that works.
If it does repeat these steps gradually going up in resolution until it breaks again, that will be the duff resolution.

Hope this helps

---

### Post by raveneffct on 2006-12-06
Woot I finally got it to work...one question though. How do I show you my xorg files? I want to make sure everything is right.

---

### Post by renzokuken on 2006-12-06
> **raveneffct said:**
> Woot I finally got it to work...one question though. How do I show you my xorg files? I want to make sure everything is right.

```
sudo gedit /etc/X11/xorg.conf
```

DONT CHANGE ANYTHING, just copy and paste everything in that file to this forum

---

### Post by bulldog on 2006-12-06
> **renzokuken said:**
> ```
sudo gedit /etc/X11/xorg.conf
```

DONT CHANGE ANYTHING, just copy and paste everything in that file to this forum

Just use cat /etc/X11/xorg.conf or gedit /etc/X11/xorg.conf,so he can't make a mistake and change something :D :D

---

### Post by raveneffct on 2006-12-06
> **renzokuken said:**
> ```
sudo gedit /etc/X11/xorg.conf
```

DONT CHANGE ANYTHING, just copy and paste everything in that file to this forum

```

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "DELL E196FP"
	HorizSync    28.0 - 49.0
	VertRefresh  43.0 - 72.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver      "vesa"
	Option	    "UseFBDev" "true"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor    "DELL E196FP"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection
```




I just want someone to tell me if everything looks about right for my machine...The video card, audio card etc etc. I don't want something to be configured wrong and not know about it. Thanks.

Dell Dimension DM051
Intel Pentium 4 cpu 3.00ghz
512mb RAM
ATI Radeon X300 128mb Hypermemory

---

### Post by d3v1ant_0n3 on 2006-12-06
From a quick glance, the video driver isn't right. It's using the vesa driver- which will display video, but not at its best. It will, at least, work basically, which is better than a constant error message- You're getting somewhere:D 

 You need a specific ati driver- I shall do a quick search and see what comes up.

*EDIT* came up with [ THIS](http://ubuntuforums.org/showthread.php?t=24557&highlight=install+ati+driver) thread - which might be a little overwhelming ( it is for me!)and [ THIS ](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) page from the wiki, that looks a little more straightforward. 

Hope thats of some help

---

### Post by raveneffct on 2006-12-06
> **d3v1ant_0n3 said:**
> From a quick glance, the video driver isn't right. It's using the vesa driver- which will display video, but not at its best. It will, at least, work basically, which is better than a constant error message- You're getting somewhere:D 

 You need a specific ati driver- I shall do a quick search and see what comes up.

*EDIT* came up with [ THIS](http://ubuntuforums.org/showthread.php?t=24557&highlight=install+ati+driver) thread - which might be a little overwhelming ( it is for me!)and [ THIS ](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) page from the wiki, that looks a little more straightforward. 

Hope thats of some help

Hey, thanks for the help. I'll check those out now. By the way, you might want to pop by again later, as I still might have this problem...you seem like a helpfull person! Thanks. Also, how do I know if my audio is set up properly.

EDIT: Oh, The wiki link you gave me. I went through this page yesterday...everything was working untill this step::
```

Confirm it worked, by issuing the "fglrxinfo" command:

    *

      fglrxinfo/glxinfo may not work properly for you via SSH and via the console when logged in as root.

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 Generic
OpenGL version string: 2.0.5755 (8.24.8)

Troubleshooting

**If fglrxinfo gives you the following, your installation is not completed correctly:**

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```


Well...guess what I got when I entered fglrxinfo, the second one. :(

---

### Post by d3v1ant_0n3 on 2006-12-06
I'm afraid I'm actually pretty useless when it comes to Ati cards- we have one on the kids' computer, but the Ubuntu install never got fully set up (they didn't 'get' linux.:rolleyes: ). Sorry! I'm lucky enough to have not really had any major issues with my modest Intel graphics.

I *did* find another wiki that might be of some use tho [HERE](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

Good luck and happy reading!

---

### Post by renzokuken on 2006-12-07
the MESA thing is a fairly common problem, and there is a solution somewhere on the wiki or on the doc storage facility.

i'll see if i can find it but im sure its at [http://doc.gwos.org](http://doc.gwos.org)

EDIT: its not the one i saw the other day but this has a solution [http://blogs.developerfusion.co.uk/blogs/thushan/archive/2006/09/01/1378.aspx](http://blogs.developerfusion.co.uk/blogs/thushan/archive/2006/09/01/1378.aspx)

Double EDIT: [http://www.ubuntuforums.org/showthread.php?t=143283&highlight=howto+ati+fglrx+mesa](http://www.ubuntuforums.org/showthread.php?t=143283&highlight=howto+ati+fglrx+mesa)

---

