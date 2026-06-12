---
title: "Setting up Device, Monitor and Screen section in xorg.conf"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by k.eight.a on 2008-09-15
**Hello,

I'm new to the Linux world. I use Ubuntu Linux 8.04 LTS for 1 week and a few days...

I had a trouble with the grapihic driver and settings of my monitor but after a suggestion new instalation solved it for me.

Unfortunately not everything is allright.

I asked for help at my local Ubuntu forums but there were not enough people who were able to help me so this is the reason why I'm here.

On 4th september my Windows XP instalation ceased to exist. I tried Live CD - the 1st boot was OK, except for the resolution used. It was visible but inconvenient either for my CRT monitor or my GPU or maybe both. 2nd and 3rd boot was not successful because the desktop was "invisible" because of the settings and resolution automatically chosen.

I made a backup and parted the primary partion C: to Linux ext3 and a Linux swap according to my RAM memory size. I had 512 MB so I used 768 MB for Linux swap partition. And then installed Ubuntu on my hard drive. 1st boot was the same as with the Live CD, so the login page was in a inconvenient resolution or setting and it is still up to now.:confused:

After login it was OK, I was able to switch the resolutions and refresh rates but when I decided to try out proprietary ATi Catalyst drivers everything went wrong and ended by the new fresh instalation.

I bought additional 2 modules of 1GB DDR RAM so I deleted the Linux swap. The second instalation I made was this saturday. Except for the login page I have no issues that can't be solved.

I have a Sapphire ATi Radeon 9600 XT GPU with 256 MB DDR, although it is visible as RV350 (Radeon 9600 / Pro) and also as a mobility version. :confused: 
[Here](http://www.techpowerup.com/gpuz/wqwm7/) are the information and below is information from terminal:```
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc M10 NQ [Radeon Mobility 9600] [1002:4e51]
03:00.1 Display controller: ATI Technologies Inc M10 NQ [Radeon Mobility 9600] (Secondary)
```...though I don't have any secondary VGA, and I have an old 17" CRT monitor Hyundai ImageQuest Q790.

So my system runs the DRI drivers:```
~$ glxinfo |grep vendor

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
```I have first modified *xorg.conf* Device and Screen sections to:```
Section	"Device"
	Identifier	"ATI 3D"
	Driver		"ati"
	Option		"VideoOverlay" "on"
	Option		"OpenGLOverlay" "off"
EndSection

...

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI 3D"
EndSection
```This worked well but I wanted to optimalize the settings for my GPU and CRT...

But still the login page uses the resolution 1440x900 that is wide-angle, so my CRT displays it inappropriately up to now...

I used information from [The open source ATI driver (xserver-xorg-video-ati)](https://help.ubuntu.com/community/RadeonDriver) and [X.Org Wiki - radeon](http://wiki.x.org/wiki/radeon) guides for ATi Radeon GPUs and I modified the graphic settings in *xorg.conf* according the them:```
Section	"Device"
	Identifier	"Radeon 9600"
	Driver		"ati"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	BusID		"PCI:3:0:0"
	Option		"AGPMode"	"8"		#usually not needed, the driver will use the setting from BIOS
	Option		"AccelMethod"	"XAA"		#either XAA or EXA. "XAA" is the default and safe choice
	Option		"DDCMode"	"on"		#Force to use the modes queried from the connected monitor. The default is off.
	Option		"ColorTiling"	"on"
	Option		"EnablePageFlip"	"true"	#only works with accelmethod "XAA"
	Option		"AccelDFS"	"true"		#seemed to speed things up using EXA acceleration
	Option		"TripleBuffer"	"true"		#This *might* help if you use something like Beryl and have slow video playback.
	Option		"DynamicClocks"	"on"		#This is for laptop users, it saves energy when in battery mode.
	Option		"DMAForXv"	"true"		#This can speed up movie playback but can in rare cases case instability
	Option		"GARTSize"	"64"		#This is the size of the "GART" that xorg will use.
EndSection

Section "Monitor"
	Identifier	"Q790"
	Vendorname	"Hyundai Electronics Industries Co., Ltd."
	Modelname	"Hyundai ImageQuest Q790"
	Option		"DPMS"
	DisplaySize	320 240		# xrandr -q 304 228 x 270 203
	Horizsync	30.0-97.0
	Vertrefresh	50.0-150.0
	"1152x864@85" "1024x768@85" "832x624@75" "800x600@85" "640x480@100" "1280x960@85" "1400x1050@85" "1600x1200@75"	# maybe "1152x864@75"	"1400x1050@75"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Radeon 9600"
	Monitor		"Q790"
	DefaultDepth	24
	SubSection	"Display"
		Depth		24
		Modes		"1152x864@85" "1024x768@85" "832x624@75" "800x600@85" "640x480@100" "1280x960@85" "1400x1050@85" "1600x1200@75"	# maybe "1152x864@75"	"1400x1050@75"
        EndSubSection
EndSection

Section	"ServerLayout"
	Option		"AIGLX"		"true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section	"DRI"
	Group	0
	Mode 0666
EndSection

Section	"Extensions"
	Option "Composite" "Enable"
EndSection
```After reboot my Ubuntu asked for configuring GPU and CRT from their menu and it run at 800x600 @ 60 Hz. Disaster...

So I started to experiment to what is the problem...

Up to now I haven't tried all the possibilities, but I found out, that the problem lies, at least partially in:```
	Modes		"1152x864@85" "1024x768@85" "832x624@75" "800x600@85" "640x480@100" "1280x960@85" "1400x1050@85" "1600x1200@75"	# "1152x864@75"	"1400x1050@75"
```But the problem is that I don't have any clue what is wrong with them. All of them are in 4:3 aspect ratio and my CRT should be able to display them all, see:```
kejta@K8-desktop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1920 x 1200
VGA-0 connected 1152x864+0+0 (normal left inverted right x axis y axis) 320mm x 240mm
   1920x1200      72.8     60.0  
   1600x1200      75.0     75.0     70.0     65.0     60.0  
   1680x1050      60.0  
   1600x1024      60.0  
   1400x1050      85.3     74.8     70.0     60.0  
   1280x1024      84.8     85.0     75.0     60.0  
   1440x900       60.2  
   1280x960       85.0     60.0  
   1280x800       60.0  
   1152x864       85.1*    75.0     74.8  
   1280x768       60.0  
   1152x768       54.8  
   1024x768       84.9     85.0     75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        84.9     85.1     72.2     75.0     60.3     56.2  
   640x480       100.0     85.0     75.0     72.8     75.0     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)
```

The problem with the login / start page is not solved and so I thought that entering the settings in the *Monitor* and *Screen* sections for the supported resolutions and refresh rates to *xorg.conf*, it will solve the problem. Instead I received the negation so it was wracked more than before! :D

I will really apperciate if there will be someone willing to follow my settings of GPU and CRT in *xorg.conf* row by row and write down any suggestions or remarks here...

---

### Post by k.eight.a on 2008-09-16
I tried so hard to describe my problem in the most possible detail and except for 33 views no one noticed and have anything to reply? :neutral:

This is not what I have expected from the infamous most friendy and helpful community / forum... :cry:

Seems like the beginner must help himself... 8)

---

### Post by k.eight.a on 2008-09-18
So much effort I've put in my question and noone has anything to say? :confused:
What is wrong with my question, why there in noone who have anything to say to my topic? ](*,)

---

### Post by robc02 on 2008-09-18
Have you selected your monitor type in Applications - Other - Screens and Graphics?  These threads might help:

[http://ubuntuforums.org/showthread.php?t=920838&highlight=screen+resolut]("http://ubuntuforums.org/showthread.php?t=920838&highlight=screen+resolut")

[http://ubuntuforums.org/showthread.php?t=769643&highlight=screen+resolution+terminal&page=2]("http://ubuntuforums.org/showthread.php?t=769643&highlight=screen+resolution+terminal&page=2")

---

### Post by Merovius on 2008-09-18
Afraid the best advice I can give is to get a card from Nvidia.

 I have an ATI x1650 Pro 512 Mb card that I cannot use in Ubuntu. It is better then the Nvidia card that I am using and that is quite annoying. But, no matter what I do or how I do it, it performs horribly. It will only run semi properly in 2D mode. Many others also have ATI driver issues.  The situation is improving but Nvidia is still much easier to install and configure.

---

### Post by robert shearer on 2008-09-18
Hi k.eight.a,   hope this helps.
Graphics are such a pain, so many variations of cards and monitors and mobos. The good news is that once it is done it is done! Then you can get on with enjoying Ubuntu.

Have you read this....[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It details the use and purpose of the  envyng package to auto-install and setup ATI and nvidia cards.

The envyng package is included in Hardy 8.01 and can be accessed from the Synaptic Package Manager.
Open Synaptic and use its search box to find envyng.

The version you want is envyng-gtk for the Gnome desktop.Once you select this it will automatically add envygtk-core.

Read the web-link for further info and use.

---

### Post by Merovius on 2008-09-18
Envy works well for me as does the hardware drivers manager. Just not with ATI. I did a lot of Googleing and nobody has that card (in AGP) working well. I think it may be a problem with a bridge chip as the card may have been PCIE first.

---

