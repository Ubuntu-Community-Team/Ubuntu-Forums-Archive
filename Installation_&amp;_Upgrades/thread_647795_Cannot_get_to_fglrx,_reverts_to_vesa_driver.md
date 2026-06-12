---
title: "Cannot get to fglrx, reverts to vesa driver"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by insert_name_here on 2007-12-22
I just updated to the latest fglrx using the method here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).   

However, after restarting, the computer (a Lenovo t60 with a ATI Radeon Mobility X1400 running Gutsy) gives > display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
 for fglrxinfo.  

Here's my xorg.conf: > 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Failsafe Monitor"
	VendorName   "Generic LCD Display"
	ModelName    "LCD Panel 1400x1050"
	HorizSync    31.5 - 65.5
	VertRefresh  56.0 - 65.0
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
	ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

 # 
	Identifier   "monitor1"
	Gamma        1
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Failsafe Device"
	Driver      "vesa"
	BoardName   "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
 
	Identifier  "device1"
	Driver      "vesa"
	BoardName   "vesa"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Failsafe Device"
	Monitor    "Failsafe Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1400 1050
		Depth     24
		Modes    "1280x1024@60" "1400x1050@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
	EndSubSection
EndSection

Section "Screen"

 # 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
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

Think this is a xorg.conf problem?  Or a driver problem?  

Thanks...

---

### Post by Pumalite on 2007-12-22
I heard AMD dropped support for the Linux driver. (?)

---

### Post by insert_name_here on 2007-12-22
I don't think so, Puma.  I'm not sure they offer much in the way of support anyways, besides "Here's a driver, it kinda works, do what you will"

---

### Post by Pumalite on 2007-12-22
I'm not sure, so I'll go along with you and suggest you backup you xorg.con file and then try 'ati'

---

### Post by Pumalite on 2007-12-22
Or:
Boot using PC (Intel x86) alternate install CD for Ubuntu or Kubuntu.
Start text mode installer and install Ubuntu/Kubuntu.
Finish Install and reboot.
Update package list and upgrade any packages needed.
sudo apt-get update
sudo apt-get dist-upgrade
Install fglrx closed source driver for ATI video cards.
sudo apt-get install xorg-driver-fglrx
Update loaded modules.
sudo depmod -a
Configure /etc/X11/xorg.conf
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
Reboot

---

### Post by insert_name_here on 2007-12-22
Why would I need to reinstall?  

My computer's working as it was before I tried to install fglrx.  Meaning, everything but 3d support, which is OK, I guess.

Is the xorg-driver-fglrx already the newest version (7.12)?  The whole reason I used the set of instructions above is that the repo method wouldn't work.

---

### Post by mrbeags on 2007-12-22
I had the same problem, try setting it to be the radeon driver.  That fixed it up for me.

---

### Post by insert_name_here on 2007-12-23
But on the radeon driver, can you get desktop effects?   

(No, correct?)

---

### Post by nzadLithium on 2007-12-23
follow this to install. it worked for me (im installing via binary 'blob')
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually)

if you still dont get dri because of opengl errors (i did)
then run this
sudo ln -s /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1

---

### Post by insert_name_here on 2007-12-23
That's what I followed.  And I had both the .so.1 and .so.1.2 files, so the symlinking didn't work (but it didn't need to)

---

### Post by mrbeags on 2007-12-24
I haven't tried using desktop effects, so I have no idea if it works or not under the radeon driver.

---

### Post by nzadLithium on 2007-12-24
lol sry

im thinking it might be something to do with your xorg.conf then.
it looks a bit dodgy to me. I'll check my one now and compare with yours. See if i notice anything thats wrong. atm it looks like you have to many device lines too me. that could be whats causing. Im just updating my pc with the ati card at mo (gutsy gibbon :D) so ill check it once it finishes.

---

### Post by pointone on 2007-12-24
Did you read the part entitled "A possible problem with fglrx.ko conflicts"?

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#A_possible_problem_with_fglrx.ko_conflicts](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#A_possible_problem_with_fglrx.ko_conflicts)

---

### Post by insert_name_here on 2007-12-24
I tried what you suggested, pointone, but no luck.  I still get the Mesa thing when I do fglrxinfo

---

### Post by nzadLithium on 2007-12-24
lol it seems i am having the same problem now :S was fine in feisty soon as i upgraded to gutsy it started to mesa...

---

### Post by nzadLithium on 2007-12-24
ok i got mine going again. It turns out i didnt see the line saying to remove all packages to do with fglrx before i started my new installation :D once i did that it worked fine.

---

### Post by insert_name_here on 2007-12-25
I *did* that.  Screw it, I'll wait until it gets to repos.

---

### Post by nzadLithium on 2007-12-25
im sry man but all i can suggest is that you get rid of all that duplicate stuff you've got in ur xorg. I'll post my ati pc's up so you can take a look. Just wait for me to login on other pc :D

---

### Post by nzadLithium on 2007-12-25
mmk

heres my xorg
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI RADEON X1300"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI RADEON X1300"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Modes    "1024x768"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```

set it up similar to mine get rid of all the extra stuff. the things that are most important are the screen section the extensions section and the device section. It looks like i dont have any modules loaded thats really weird i woulda thought you'd have to have opengl etc loaded to do awesome games. That could be why i get crap fps though. i think im gona try enabling opengl overlay disabling video overlay and adding some modules see if i can get my fps to go up a bit :D 

Anyway take a look at my xorg modify yours so it looks similar. Before you do anything though i would recommend you open a terminal and backup your xorg just in case it gets screwed up.
How to backup:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

restore is:
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Play round with it a bit 

Good luck

---

### Post by kikekurikapoo on 2007-12-26
to the OP.. you could try removing some stuff from you xorg.conf.. I had the same problem  with a cluttered xorg.conf and after cleaning it up a bit and removing xgl I got 7.12 working..

try removing: 

Section "Monitor"
Identifier "Failsafe Monitor"
VendorName "Generic LCD Display"
ModelName "LCD Panel 1400x1050"
HorizSync 31.5 - 65.5
VertRefresh 56.0 - 65.0
Gamma 1
ModeLine "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
ModeLine "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
ModeLine "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
ModeLine "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
ModeLine "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
ModeLine "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
ModeLine "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
EndSection

Section "Monitor"

#
Identifier "monitor1"
Gamma 1
EndSection

Section "Device"
Identifier "Failsafe Device"
Driver "vesa"
BoardName "vesa"
BusID "PCI:1:0:0"
EndSection

Section "Device"

Identifier "device1"
Driver "vesa"
BoardName "vesa"
BusID "PCI:1:0:0"
Screen 1
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Failsafe Device"
Monitor "Failsafe Monitor"
DefaultDepth 24
SubSection "Display"
Virtual 1400 1050
Depth 24
Modes "1280x1024@60" "1400x1050@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

Section "Screen"

#
Identifier "screen1"
Device "device1"
Monitor "monitor1"
DefaultDepth 24
EndSection

and maybe load "dri" in modules

that's how I got mine to work.. goodluck with yours man..

---

### Post by Dreamlocked on 2007-12-26
Ok, I posted this [here]("http://ubuntuforums.org/showthread.php?t=646697&page=2&highlight=ATI+install%2A") as well, but didn't get any answer regarding the subject.

About the guide everyone is following....
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Is it me, or did someone (accidentally and very recently) delete the passage :

Code:

```

sudo module-assistant prepare,update
sudo module-assistant build,install fglrx -f
sudo depmod -a

```

Doesn't omitting this make the whole installation process invalid? Or is it no longer needed because of the new dkms used?

---

### Post by nzadLithium on 2007-12-26
I dont think it is neccessary as i never had to do it. Plus since we are making deb packages out of it i think anything like that would be sorted out by the deb installation.

---

### Post by insert_name_here on 2007-12-27
Thanks for the advice, y'all.  

Haven't had a chance to try it yet, because I'm out of town.  I'm not really willing to put this lappy through much driver kung-fu until I get back home to a backup computer.  

I did replace (with a backup) the first suggested xorg.conf, but I haven't restarted yet.  (In 2.5 days... ahh the beauties of Linux.)

---

### Post by Don1500 on 2007-12-28
I still can't get it to work. 
>  $ fglrxinfo
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory


How do I get the lib?

---

### Post by lvleph on 2007-12-28
I was having a lot of trouble getting my ati card to work properly. I ended up using [Envy](http://albertomilone.com/nvidia_scripts1.html), and all works now.

---

### Post by insert_name_here on 2007-12-29
Hmm.

I've tried both nzadLithium and Kikekurikapoo's xorg suggestions, and still no luck.

fglrxinfo still gives mesa

modprobe dri says the module doesn't exist

Restricted Drivers Manager still says ATI accelerated graphics driver is not in use.

Any furhter ideas?

Also, does anyone know if the fglrx version in the repos is 7.12?

---

### Post by insert_name_here on 2007-12-29
> 1. Try:

modprobe -vf fglrx

If the output is something like this: "install /sbin/lrm-video fglrx"

then modify "/etc/modprobe.d/lrm-video" and comment out the line with fglrx, ie:

#install fglrx /sbin/lrm-video fglrx $CMDLINE_OPTS

On another[ thread]("http://ubuntuforums.org/showthread.php?t=645974&highlight=fglrx+mesa&page=3"), lockpicker gave that solution.

It worked for me, and fglrxinfo now gives the right answer.  I'm still working on getting Compiz running, but at least its a step in the right direction.

---

### Post by insert_name_here on 2007-12-29
And I fixed those compiz problems by changing the 0 to a 1 in my xorg.conf under the composite extension.

Ah yay! Compiz!!

Thanks, all.

---

### Post by nzadLithium on 2007-12-30
don look on the last post of the first page. i already explained what you need to do if it cant find the gl libraries :S

---

