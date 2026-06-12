---
title: "xrandr screen rotation in Gutsy"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by captainmnb on 2007-10-23
I just did a fresh install of Gutsy today on my Thinkpad X41 tablet.  Previously, with Feisty, I was able to rotate the screen with "xrandr -o left", but since the upgrade, this has no effect.  Any idea why this might be the case or how to fix it/work around it?

---

### Post by 23meg on 2007-10-23
Are you getting any errors?

---

### Post by captainmnb on 2007-10-23
Nope.  Nothing happens at all.  I just get a new input line, with no feedback.  I don't know how I would go about seeing what's actually failing.

---

### Post by 23meg on 2007-10-23
Try the --verbose option and see if you get any errors.

---

### Post by captainmnb on 2007-10-23
Here's what I get with "xrandr -o left --verbose":

>  SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 270mm x 203mm )  *58   85   75   70   60  
 1    832 x 624    ( 270mm x 203mm )   75  
 2    800 x 600    ( 270mm x 203mm )   85   72   75   60   56  
 3    640 x 480    ( 270mm x 203mm )   85   73   75   60  
 4    720 x 400    ( 270mm x 203mm )   85  
 5    640 x 400    ( 270mm x 203mm )   85  
 6    640 x 350    ( 270mm x 203mm )   85  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none
Setting size to 0, rotation to left
Setting reflection on neither axis

---

### Post by 23meg on 2007-10-23
What's the brand and model of your display device? It can also help if you post the contents your xorg.conf file.

---

### Post by giuliastro on 2007-10-27
I have an X41 + Gutsy and the screen rotates fine. The problem is the old issue about the screen freezing (not refreshing) if compiz (desktop effects) is enabled. After 1 1/2 year I haven't found a solution to this problem yet. :(

---

### Post by captainmnb on 2007-10-27
Oddly enough, xrandr now works for me.  I didn't change anything, I just rebooted once again (I had rebooted a couple times before to no avail), and suddenly it worked.  Odd.

In response to giuliastro, I of course have that same problem, but I keep a drawer with 4 launchers on my panel, one to switch to Metacity, one to switch to Compiz, one to rotate the screen left (using a shell script with xrandr and xsetwacom), and one to rotate the screen back to the normal position.  A bit cumbersome, but not terrible.

---

### Post by ApoXX on 2007-10-27
I'm also having issues on both my T4220 Tablet PC and my desktop which currently has a Geforce 7600GT card.

The tablet will rotate if I have Compiz Fusion disabled but the mouse seems to be locked into the old screen constraints, also I see screen artifacts when it's rotated and I move windows around on the screen. I've tried disabling Sync To VBlank among other options in CompizConfig to no avail.

My desktop reports a different error altogether:
```

root@Uberleet:/home/brian/.mozilla# xrandr -o inverted
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  158 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

I've tried using the new control interface:
eg. xrandr --output LVDS --rotate normal
but it didn't help anything.

Any thoughts?
Are there any alternatives to xrandr?

---

### Post by smurtguy on 2007-10-29
welcome to the poorly documented world of randr extention version 1.2
its the magical version that is supposed to solve everyone's woes that want to have multiple monitors
and its the magical version that screws us that just want to rotate our single monitor
Don't you feel the magic already? whhheeee

well from what I can tell there should be a way to use the new randr to rotate a screen, but I cannot find it.

There something fundamental missing from my xorg.conf file I think that would allow rotation
since is I run xrandr -q 
it lists nothing about being able to rotate the screen, where as everyone else's shows that it allows them to do so. Of course they are all dealing with 2+ monitors. 

So maybe we're just SOL here.In all orgasmic joy of setting up 2 monitors they overlooked the fact that us simple joyless 1 monitor folk can't rotate our monitor anymore.

I think there is a way to for xrandr to use the 1.1 version options.
I did something like that with 7.10 beta I think and it worked ok, except that it would not go into the invereted rotation.

now however I can't seem to get that to work. Please doing so requires setting an option that appearantly turns off some or all acceleration features.

possibly try adding Option "RandRRotation" "true"
to the screens section of you xorg.conf

---

### Post by smurtguy on 2007-10-29
man xrandr 1.2 is really pissing me off

I've been looking for a few days now, for information on how to get it rotate a single screen properly.
And all I see are posts gushing on and on about how great it works. However none of the posts go into any depth on what config requirements the new randr extension has. AND not a single one actually is trying to rotate a screen. 

the randr extension is now multidisplay extension.

I really wonder if the 1.2 screen rotation even works.

You can add the line

Option "RandRRotation" "true"

to the screen section.

This will allow the old style rotation to seem to work.
I say seem because you are quite likely to have the window manager still think the display has not been rotated.

btw once the above line is set, you get a different error when you try 

xrandr --output default --rotate left

it will tell you that there is no mode for "1050x1400"

so does this mean we need to setup up additional mode lines in xorg.conf?
If so, how do we specify the which 1050x1400 is the left rotation and which is the right rotation
plus how do we add the line for the inverted screen. 1400x1050 is there

BTW another fun thing about xrandr now is that if you use an invalid "output" it won't generate an error.

so 

xrandr --output GARBAGE --rotate left

doesn't do anything, even complain that this is  not a valid output


So where can we find some documetation that explains what we need to do get xrandr to do what everyone claims it does?

I really do want to know what it really takes to set this up

I guess I'll try the extra mode line, but personally I think having to do that is pretty crappy.
1) because there is no clear documentation that I can find describing what is needed
2) because no non-linux-guru will ever want to put with this this much garbage just to rotate a screen.

If rotation is enabled for a display of resolution 1400x1050, this needs to imply then that 1050x1400 will exist

Finally I think KDE doesn't really support randr. Even with 7.04, a rotated screen displays repeated visual errors. With SUSE and 7.10 beta it doesn't even respond to xrandr anymore

ok last bit to my rant

X's configuration IMO is the biggest hindrance to general linux adoption

---

### Post by PhantamaroK on 2007-10-31
smurtguy, I read your post nodding my head the whole time.

I can't for the life of me figure out how to get rotation working in Gusty and can't believe that it's not a bigger issue amongst users.  As bad as it sounds, I'm glad to finally find people with a similar problem.  What a waste of a tablet it is (I have a Thinkpad X61) to not be able to rotate my screen.

I really think, at least for me, that it's an issue with Compiz Fusion.  I have a T60 running Xubuntu 7.10 on which rotation (xrandr) seems to be working fine, and I'm seriously considering just loading xubuntu on my X61.  It's awesome to be able to show off useless animations to people who have never seen them before, but I spend so much more time frustrated with a landscape tablet than I do showing off a rotating cube.

---

### Post by george1984 on 2007-11-11
Hello. I am a non-technical novice. This thread has solved my problem. Thanks.

	Rotation now works in Gutsy. It does not work in Feisty, but I have not not attempted the change to xorg.conf in Feisty as this is my main install, and I do rather mess things up, and I am about to change to Gutsy anyway.

	Equipment – Graphics card...Geforce 7300 LE/PCI ( proprietary driver)
		          Screen – HP LP2065 (with pivot function)

	System>Preferences>Screen Resolution...Rotation function was greyed-out.
	In a terminal...xrandr -o left... produced this message (actually I have just generated this in Feisty which is where I am right now, But I think it is identical) 

george@MrGrumpy-01:~$ xrandr -o left 
X Error of failed request:  BadMatch (invalid parameter attributes) 
  Major opcode of failed request:  156 (RANDR) 
  Minor opcode of failed request:  2 (RRSetScreenConfig) 
  Serial number of failed request:  12 
  Current serial number in output stream:  12 
george@MrGrumpy-01:~$ 

	Next, Examine the contents of /var/log/Xorg.0.log
	The relevant lines were present, namely:-
		(--)  RandR enabled
            (II)  Initializing built-in extension RANDR

	This seems to indicate that the card driver ( nvidia propriatory ) is capable.

	Next examine the xorg.conf file
	There is no reference to Xrandr, or any rotation capability.

	Next add the line... Option  “RandRRotation”  “True”
	This is how xorg.conf now looks :-


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
	Option		"XkbLayout"	"gb" 
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

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"stylus" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"stylus" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"eraser" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"eraser" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"cursor" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"cursor" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "Device" 
	Identifier	"nVidia Corporation G72 [GeForce 7300 LE]" 
	Driver		"nvidia" 
	Busid		"PCI:1:0:0" 
	Option		"AddARGBVisuals"	"True" 
	Option		"AddARGBGLXVisuals"	"True" 
	Option		"NoLogo"	"True" 
	Option		"RandRRotation"		"True" 
EndSection 

Section "Monitor" 
	Identifier	"HP LP2065" 
	Option		"DPMS" 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"nVidia Corporation G72 [GeForce 7300 LE]" 
	Monitor		"HP LP2065" 
	Defaultdepth	24 
	SubSection "Display" 
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1024x768"	"800x600"	"720x400"	"640x480" 
	EndSubSection 
EndSection 

Section "ServerLayout" 
	Identifier	"Default Layout" 
  screen "Default Screen" 
	Inputdevice	"Generic Keyboard" 
	Inputdevice	"Configured Mouse" 
	 
	# Uncomment if you have a wacom tablet 
	#	InputDevice     "stylus"	"SendCoreEvents" 
	#	InputDevice     "cursor"	"SendCoreEvents" 
	#	InputDevice     "eraser"	"SendCoreEvents" 
EndSection 
Section "Module" 
	Load		"glx" 
EndSection

	Reboot...and now Rotation works! Really chuffed.

				Regards
                                                     George

---

### Post by Mormiriel on 2007-11-16
Ahh.. xrandr. I had this working perfectly (for me and my Toshiba Satellite Tablet) in my Kubuntu Fiesty. I thought Gutsy sounded like a great idea... but now I'm not sure...

I've had to tweak my old script to make things rotate when I turn the screen. I had to change the xorg again (which I expected I'd have to do), however the rotation does not work properly.

When I rotate with command line or by turning the screen, the display rotates, *but* the display doesn't switch to a portrait mode, thus making it really hard for me to take notes. :-(

From my cursory looks, it seems that no one has a solution for this yet. Darn me and my not checking out  the whines before upgrading.

---

### Post by george1984 on 2007-11-18
Sorry to hear about your misfortune.

Just to confirm that on my equipment when I do "xrandr -o right" it rotates and changes from 1600x1200 to 1200x1600, realizing the full potential of my new LP2065 display

                                            Regards
                                                George

---

### Post by Gaiwecoor on 2007-11-29
> **Mormiriel said:**
> ...
When I rotate with command line or by turning the screen, the display rotates, *but* the display doesn't switch to a portrait mode, thus making it really hard for me to take notes. :-(
...


Mostly the same problem here, on an Acer TravelMate C300.

I'm running Kubuntu 7.10, and the resolution doesn't change (remains 1024x768, rather than switching to 768x1024) when I rotate the screen.  This is my problem when using Kwin as the window manager.  When using Compiz, the resolution will change as expected, but the windows don't update themselves.  For example: when writing in a document, the changes will not appear until you switch to another window, then switch back.  (This problem doesn't occur in Kwin)

Any recommendations?

---

### Post by Mormiriel on 2007-11-29
It seems that thus far a lot of people have similar problems, but there is no fix.

---

### Post by DonaldPK on 2007-12-08
i have it working in a default Ubuntu 7.10 installation on a Fujitsu U1010 mini laptop. no special settings in Xorg.conf except for some extra lines to get the touchscreen working.

it can show Normal and Inverted using System > Preferences > Screen Resolution > Rotation and also Left and Right but in those 2 modes, the cursor movement doesn't seem to follow the mouse or the touchscreen. needs some work.

---

### Post by henriquemaia on 2007-12-16
> **DonaldPK said:**
> i have it working in a default Ubuntu 7.10 installation on a Fujitsu U1010 mini laptop. no special settings in Xorg.conf except for some extra lines to get the touchscreen working.

it can show Normal and Inverted using System > Preferences > Screen Resolution > Rotation and also Left and Right but in those 2 modes, the cursor movement doesn't seem to follow the mouse or the touchscreen. needs some work.

I have the same experience here. The mouse movement is not working properly when X is rotated. Any ideas on how to solve this?

---

### Post by zackiv31 on 2007-12-16
I just stumbled upon this thread as I try to get my X61 tablet rotation working correctly, and it doesn't look like things are working out well for us :-/

Rotation through the menu works good (X must be updated and redrawn, but it correctly changes my resolution.

My stylus does not work when rotated... the pointer mirrors where I touch on the screen, meaning that the stylus drivers must be made aware of the change, but I have no idea how to remedy this.


Is there any other information out there for this problem?

Also is there a journal format that can be used with both Vista and Linux?  Right now I'm using xournal for ubuntu, and it works great... I just wish I could share the files between both my OS's easily.

---

### Post by Gaiwecoor on 2007-12-16
> **zackiv31 said:**
> ...
My stylus does not work when rotated... the pointer mirrors where I touch on the screen, meaning that the stylus drivers must be made aware of the change, but I have no idea how to remedy this.

Is there any other information out there for this problem?

I believe you're looking for this:

```
xsetwacom set stylus Rotate ccw
xsetwacom set eraser Rotate ccw
xsetwacom set cursor Rotate ccw
```

If I recall correctly, the Rotate option could be cw, ccw or none.

> **zackiv31 said:**
> ...
Also is there a journal format that can be used with both Vista and Linux?  Right now I'm using xournal for ubuntu, and it works great... I just wish I could share the files between both my OS's easily.

The only one I know if is Jarnal.  [[link]("http://www.dklevine.com/general/software/tc1000/jarnal.htm")]  As far as I know, it uses the same format as Xournal and Gournal, but it can be run cross-platform, as it's a java implementation.

Hope that helps!

---

### Post by zackiv31 on 2007-12-17
Is there a way to have those commands execute on rotate?

Currently I'm doing it through the Screen Resolution, or whatever it is options... and doing it through there...

Ideally I would not like to use that, and use the rotate button on the X61 itself... meaning each time i press it, everything rotates left... and at the same time executes that command you just described.

Has this been achieved yet?

---

### Post by Gaiwecoor on 2007-12-17
Honestly, I don't really know much more than what I've been able to find on these forums.  This thread might be what you're looking for, though:   [Howto: Get automatic xrandr screen rotation on a Thinkpad X61 tablet/Intel 965]("http://ubuntuforums.org/showthread.php?t=604896")

I believe they get it to rotate the screen when you swivel it, but I didn't see anything about the button, sorry.  Alternatively, someone somewhere posted this script that does the rotating when called:

```

#!/bin/bash

if [ -e ~/.rotated ]
then
        xrandr -o normal
        xsetwacom set stylus Rotate none
        xsetwacom set eraser Rotate none
        xsetwacom set cursor Rotate none

        xsetwacom set stylus BottomX 28800
        xsetwacom set eraser BottomX 28800
        xsetwacom set cursor BottomX 28800

        xsetwacom set stylus BottomY 21760
        xsetwacom set eraser BottomY 21760
        xsetwacom set cursor BottomY 21760

        rm ~/.rotated

else
        xrandr -o left
        xsetwacom set stylus Rotate ccw
        xsetwacom set eraser Rotate ccw
        xsetwacom set cursor Rotate ccw

        xsetwacom set stylus BottomX 21760
        xsetwacom set eraser BottomX 21760
        xsetwacom set cursor BottomX 21760

        xsetwacom set stylus BottomY 28800
        xsetwacom set eraser BottomY 28000
        xsetwacom set cursor BottomY 28800

        touch ~/.rotated

fi

```

Hope it helps.

---

### Post by Centx on 2008-01-05
Hoping to see this post with a [SOLVED] tag, I'll try to share my experiences with xrandr and xorg.conf using "nvidia" drivers =)

I was messing around in xorg to get xrandr working searching google and everywhere, and a "cat /var/log/Xorg.0.log |grep -i randr" showed ```
(**) NVIDIA(0): Option "RandRRotation" "True"
(==) RandR enabled
(II) Initializing built-in extension RANDR

```but this was actually not right (I think at least). It seems that I had several definitions of both Screens, Device and a messed up serverlayout due to some experimenting with duel head earlier last year, using mostly the "nvidia-settings" utility. 

Now what I did to resolve this was removing _all_ that I thought was unnessecary, the wacom and all, and only left one definition of screen, device and so. Now the output from the above log-check was the same, but lo' and behold, now xrandr -o left did not yeild an error, but worked! 

So here is my xorg.conf, and this _works_ (for me at least)
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen       "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "1"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Monitor"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection


Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Option       "RandRRotation" "True"    
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1440x900" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1440x900" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1440x900" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1440x900" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1440x900" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

```

---

### Post by sgf323 on 2008-01-23
I'm new to Ubuntu and thanks to everyone in this thread I got this working!  I'm running Gutsy with a 6600GT.

Here's what I had to do to get it working:

First, in terminal:

```
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
sudo nvidia-glx-config enable
sudo nvidia-xconfig
```

Then I opened xorg.conf and added: Option "RandRRotation" "True" 

That got it working but not at proper resolutions.  I was stuck at 1024x768 on my Hanns-G 19" widescreen.  So, next I edited the xorg.conf file again to add 1440x900 and after a restart I was able to get the resolution I wanted and rotation!

I've got this monitor along side my XP machine with a 28" monitor.  I plan on using Synergy to work between both.  The 19" on it's side is the exact height of the 28" monitor so they look really good next to each other.

I just wish that there was something like MaxiVista for Ubuntu!  -- I don't really feel like installing XP on my extra machine just to run MaxiVista.  I'm going to try out Synergy for a while and see how I like it.

---

### Post by Hilko on 2008-02-15
When I had Feisty, my screen rotation worked fine. Since I have Gutsy I cant get it working anymore. I just want to be able to rotate my screen again.

Here is a part of my xorg.conf:
...
Section "Device"
	Identifier	"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Driver		"via"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
	Option		"RandRRotate"		"true"
	#Option		"Rotate"		"CCW"
EndSection

Section "Monitor"
	Identifier	"AL1923"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
	Monitor		"AL1923"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes
...

I don't know what nvidia is, but I think I don't have it (whatever it is). I don't know if that is relevant.

Please, if anyone could explain how I can rotate my screen, it would make me very happy.

---

