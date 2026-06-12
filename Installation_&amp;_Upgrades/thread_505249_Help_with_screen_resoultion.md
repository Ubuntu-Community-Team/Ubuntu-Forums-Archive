---
title: "Help with screen resoultion"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by bail_w on 2007-07-20
Hi, i am new to ubuntu and i just install 7.04 but i want to change the screen resolution to 1900 x 1200  instead of 1280 x1024 (maximum on the list).

Here is my system spec:

Intel E2140
Asus P5b
Dell 2405FPW
ATI X800XL PCI-E
2GB Ram

Thanks

---

### Post by Herman on 2007-07-20
The screen resolutions that are available for us to select from in 'System'-->'Preferences'-->'Screen Resolution' are controlled by a text file called /etc/X11/xorg.conf, and you can edit that file with gedit text editor or another text editor of your choice.
You should make a backup copy of the file first, to be safe,
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```Then you can open the file and edit it as you think best. 
```
sudo gedit /etc/X11/xorg.conf/
```You should be able to paste "1900x1200" in the mode lines there (list of resolutions). Are you sure it's "1900x1200", or would it be "1920x1200"?
For example, here's what mine looks like now,
```
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc RV280 [Radeon 9200 SE]"
    Monitor        "AL2016W"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        [COLOR=Red]**[COLOR=Sienna]"1920x1200"[/COLOR] **[/COLOR]"1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes       [COLOR=Red]**[COLOR=Sienna]"1920x1200"[/COLOR] **[/COLOR] "1680x1050" "1280x800" "1152x720" "800x500" 
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        [COLOR=Red]**[COLOR=Sienna]"1920x1200"[/COLOR] **[/COLOR] "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        [COLOR=Red]**[COLOR=Sienna]"1920x1200"[/COLOR] **[/COLOR] "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        [COLOR=Red]**[COLOR=Sienna]"1920x1200"[/COLOR] **[/COLOR]"1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes       [COLOR=Red]**[COLOR=Sienna]"1920x1200"[/COLOR] **[/COLOR] "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
```If you aren't sure you understand what I mean and you need more help with that, just ask me and I'll try to explain it better.

If you have trouble and you can't boot into the Ubuntu desktop anymore (if you made a mistake), here's how you can use your Live CD like this to mount your Ubuntu install, get your /etc/X11/xorg.conf and edit it again to rescue your system if needed, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

 Regards, Herman :)

[COLOR=Red][B]EDIT: This will only be useful if the resolutions you are pasting in are supported by your hardware and software (drivers).

[/B][COLOR=Black]A useful command to see what resolutions will be supported by your hardware is 'sudo ddcprobe'
[/COLOR][/COLOR]```
sudo ddcprobe
```As for what resolutions whatever your combination of hardware and the driver you are using is capable of,  that's another matter.

---

### Post by bail_w on 2007-07-20
okay i pasted in the conf file and then?

Edit: i save it and exit. but i still cant see any option of "1920x 1200" under screen resoultion?

Edit: after i save and restart now i cant boot up to the ubuntu desktop

---

### Post by Herman on 2007-07-20
If you have trouble and you can't boot into the Ubuntu desktop anymore (if you made a mistake), here's how you can use your Live CD like this to mount your Ubuntu install, get your /etc/X11/xorg.conf and edit it again to rescue your system if needed, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

---

### Post by rmadd on 2007-11-01
Herman I have read your post to Bail_w, as I am having the same problem. I did as you said and 
went to terminal and entered  sudo gedit /etc/X11/xorg.conf/, and entered my resolution that I want on my laptop, 1280x1024, 1280x800 was already logged in this file, but in "preferences-screen resolution is 1024X768, this is not logged in the gedit file. After doing what you said I restarted the machine with the same results, 1024x768 in the screen resolution. Ive tried every way I can find and so far nothing. Hope you can help. Thanks RM

---

### Post by Herman on 2007-11-01
Hello rmadd,
The advice I gave to bail_w should work and help anyone else with a similar problem too.
I'm wondering if I explained everything in enough detail though. Maybe I should have said to make sure you find the 'mode line' or lines, down near the bottom of the file under the heading 'Section "Screen", and to paste the desired resolutions in there. Of course you would only do that if you know your hardware can support those resolutions. I can't imagine what else could go wrong, notwithstanding Murphy's Laws. :)

If you can post a copy of your /etc/X11/xorg.conf file here please, I  will take a look at it and see if I can help you, or someone else can if they want.

Regards, Herman :)

EDIT: So when you went 'System'-->'Preferences'-->'Screen Resolution', and you got the 'Screen Resolution Preferences' panel, and you saw the spinbox titled 'Resolution', what happened when you clicked on it?
Did you not get a list of the resolutions you have in your mode line or lines in /etc/X11/xorg.conf?

[COLOR=Red][B]EDIT: This will only be useful if the resolutions you are pasting in are supported by your hardware and software (drivers).

[/B][COLOR=Black]A useful command to see what resolutions will be supported by your hardware is 'sudo ddcprobe'
[/COLOR][/COLOR]```
     sudo ddcprobe 
```
As for what resolutions whatever your combination of hardware and the driver you are using is capable of, that's another matter.

---

### Post by Desd on 2007-11-01
Hey, I am not alone here!

Sorry to jump in, but this is what I have been experiencing the last days...

I am on my laptop Asus F3m with a 15,4 widescreen 1280x800 and I don't get it to display right. Every change I make seems senseless since at start up my computer tells me that it can not detect my screen and graphicscard properly. I've checked it, xorg.conf should be fine.

Here is what I did
System -> Administration -> Screens and Graphics
Choose the appropriate settings (i.e. the screen res and right graphicscard (Nvidia)
Hit save and see what happens (nothing)

Then System -> preferences -> Screen resolution
Try to choose the right resolution, but it only says 800x600 and 640x480
Cry and weep over this, search ubuntuforums.org

sudo gedit xorg.conf
Get this:
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation MCP51 PCI-X GeForce Go 6100"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generieke beeldscherm"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation MCP51 PCI-X GeForce Go 6100"
	Monitor		"Generieke beeldscherm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection
```

Sit back, scratch my head, search ubuntuforums again and wonder what went wrong.
I've tried install a new Nvidia driver from Nvidia.com, Envy, sudo dpkg-reconfigure xserver-xorg, dealing with the vesa driver. But all with zero result. When I go to System -> preferences -> Screen resolution it only gives me the options 800 and 640. When I start up my computer it tells me that it can not detect my graphicscard and screen properly and it asks me whether I'd like to configure this (so I do that, with no result) or run in low graphics mode.

It does this since 7.10. 7.04 was fine, installing the appropriatery drivers and there I went. I've done an upgrade from a fresh 7.04 install to 7.10. My system won't start up with the latest kernel, so I've changed the boot order so it runs on 2.6.20-16-generic.

I have got no clue on what to do now, so help is appreciated!
Thanks in advance!


Desd

---

### Post by rmadd on 2007-11-02
Herman, went back and followed you instructions, they worked this time. Thanks for you help. RM

---

### Post by Herman on 2007-11-03
rmadd,
Thanks for your feedback, I'm glad it worked for you.

Desd,
I'm not sure about your problem. Yours seems to be a little more complicated.
What result do you get from the command 'sudo ddcprobe?'
```
sudo ddcprobe
```

Your Asus F3m isn't in the Ubuntu supported laptops list, made by the laptop testing team, [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam). That doesn't mean it isn't supported, or is impossible to configure. There are lots of laptops that aren't in the list but which work perfectly under Ubuntu. If it was in the list though, we might be able to get helpful clues from the notes under someone's review.  
Try reading about similar models of Asus laptops that did get tested and see if there is anything useful written there that might help you.

This page, [http://www.linux-on-laptops.com/asus.html](http://www.linux-on-laptops.com/asus.html) does list some similar  but not identical models of  Asus laptops where we can look for clues, here are the ones I mean,[LIST]
[*][Asus F3JM]("http://forums.fedora-fr.org/viewtopic.php?pid=99959") [Fedora Core 5] (in French)
[*][Asus F3JM]("http://gentoo-wiki.com/HARDWARE_Asus_F3JM") [Gentoo]
[*][Asus F3Jm]("http://olivaux.free.fr/index.php/post/2007/02/01/Installation-linux-sur-un-ASUS-F3JM-AK022H") [openSuse] (in French)
[*][Asus F3Jm]("http://www.w1ldt4ng3nt.net/blog/item/77") [Ubuntu 6.10][/LIST]I am guessing after reading those that maybe you should try going for 1680 x 1050 resolution and see if that will work.
Maybe try a mode line like:
```
 "1680x1050" "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"

```..unless their Asus F3Jm 15.4" monitors are different from your Asus F3m15.4" monitor. Maybe I'm being a lot over-optimistic though. It's worth a try but not guaranteed. 
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
    Driver        "nvidia"
    BusID        "PCI:0:5:0"
EndSection

Section "Monitor"
    Identifier    "Generieke beeldscherm"
    Option        "DPMS"
    HorizSync    30-80
    VertRefresh    50-120
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
    Monitor        "Generieke beeldscherm"
    DefaultDepth    24
    SubSection "Display"
        Modes           "1680x1050" "1600x1200" "1360x850" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"

# Uncomment if you have a wacom tablet
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection
```


Regards, Herman :)

---

### Post by Desd on 2007-11-04
Hi Herman,

Since I had a major problem with my first upgrade to 7.10 (partly due to me :oops: ) I had reinstalled 7.04 fresh again and from there upgraded to 7.10 (7.10 LiveCD would not boot on this machine, unlike on others, that might have been a sign). I've screened the forums and think that 7.10 is not for me now, so I've downgraded to 7.04 again and will stay there. 7.04 does what I want and I can live without the nice features of 7.10.

I am now looking at this forum again in 1280 x 800 and am SOOO happy with that. I need my laptop for presentation purposes too, so the res is crucial for me. And I don't think that anybody wants 800x600 when the screen can do more, would they?

Thanks for the suggestions. I'll be there when we go to 8.x and hope for better screen & graphic support. 

Thank you,

Desd

---

### Post by Herman on 2007-11-04
Hello Desd,
Well I don't blame you for going back to Feisty Fawn, given those circumstances, that's for sure.
You know, I still have Feisty Fawn in my computers. Instead of upgrading, I just installed Gutsy Gibbon in a new partition beside Feisty, so if anything doesn't work yet in Gusty, I can just boot back into Feisty whenever I need to.

I have found that to be a better tactic than simply upgrading, as long as there is enough hard drive space in the computer for that. That allows me lots of time to make sure the new release will do everything I need before I transfer all my files from the old Ubuntu to the new one.

It's possible these days to resize Linux partitions and move them around from the start point as well as just the end of the partition with modern versions of GParted. If someone wanted to, (if they don't have a large hard drive like I do), then they can install the latest release in a small partition, test the new install, and resize one partition larger and the other smaller a little at a time as they transfer their data.

Usually there are updates that fix various problems as the more recent release matures, especially during the first few weeks after the release date. You wouldn't want to be waiting around for one though, especially if you have work to do.

I was lucky with Gutsy Gibbon, it worked right in all my computers, even in my newest computer with my nice new Acer AL2016W  1680 x 1050 monitor. When I was moving from Edgy Eft to Feisty Fawn I had to edit /etc/x11/xorg.conf by hand for that monitor, but not with Gutsy Gibbon.
I'm finding Gutsy Gibbon much better than Feisty, but there are few little annoyances that might be fixed as time goes on.

I'll be sticking with multiple booting rather than upgrading when the next release comes out too.

Regards, Herman :)

---

### Post by Desd on 2007-11-04
Hi Herman,

Thanks for the tip... That is a very simple, but very, very good idea... I've lost quite a bit of time with this fuzzling around. Next time I'll use your tip and save some, won't I?

It might even be a good idea to have your data in a seperate partition, which can be accessed by any OS from another partition (well, any OS...). 

Keep up the good work, 
Regards,


Desd

---

### Post by Stebbins on 2007-11-05
I have two computers with Ubuntu installed on them, and am having screen resolution problems with both.  One of them only has 2 resolution options: 800x600 and 640x480.  The other has a widescreen monitor, but no widescreen resolution options.  I tried editing the xorg.conf file for both of these computers, and... it didn't work in either case.

Here is the relevant part of xorg.conf for the computer that only gives the two resolution options:
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Am I doing something wrong?

---

### Post by bulldog on 2007-11-05
Did you try and install a graphics driver like nvidia or ati?
Don't know which kind of graphics you have,but a driver will help.
If it's a nvidia or ati graphics,maybe envy can help you.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Desd on 2007-11-06
Hi Stebbins

Before going envy, you could try to reconfigure by ```
sudo dpkg-reconfigure xserver-xorg
``` in your terminal screen.This will guide you trough the configuration of your screen and graphic card. 
Also, if you have Nvidia or Ati, you could see if it is enabled by going to System -> Administration -> restricted drivers (or something like that, I use a translated Ubuntu). If not, enable it and Ubuntu will install whatever you need (that is, if your more lucky than me...)

Good luck!


Desd

---

### Post by Stebbins on 2007-11-09
I ran dpkg-reconfigure, and it worked for my widescreen monitor.  My other computer's resolution is limited by the graphics card.  Thanks for your help.

---

