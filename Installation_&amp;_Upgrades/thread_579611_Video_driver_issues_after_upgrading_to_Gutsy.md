---
title: "Video driver issues after upgrading to Gutsy"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by dweez on 2007-10-18
I upgraded to Gutsy (from Feisty) on my laptop yesterday (figured I'd get most of the updates before the rush today) and now I'm having a weird issue with the video driver.  Besides the fact that my laptop screen isn't being detected (I can't remember if Feisty detected it properly or not but I do know that the resolution and everything was right), when I try to install the Restricted Driver for my video card I get the error in the screenshot below.  I've ran apt-get clean and apt-get -f install but no luck.

Anyone else run into something like this and have an idea what I need to do?

Pertinent System Specs:
Dell Latitude D820
15.4" WUXGA screen
nVidia Quadro NVS 120 w/512MB (256MB dedicated)

[[IMG]http://img502.imageshack.us/img502/548/erroroo6.th.png[/IMG]]("http://img502.imageshack.us/my.php?image=erroroo6.png")

---

### Post by linkagge on 2007-10-18
i'm in the middle of my upgrade and I got a similar error while it was installing, but mine said.

could not install 'var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb'

the upgrade will continue but the 'var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb'
package may be in a not working state. please consider submitting a bugreport about it.

subprocess pre-installation script returned error exit status 2

so I guess i'll just have to wait and see what happens but I figure that I hopfully can just run envy after the install is finished and hope that it fixes my issues.

Please let us know how you fix your problem.

Thanks !!

---

### Post by mikec13 on 2007-10-18
> **dweez said:**
> 
Pertinent System Specs:
Dell Latitude D820
15.4" WUXGA screen
nVidia Quadro NVS 120 w/512MB (256MB dedicated)

I've got the exact same setup, and my restricted driver installed without a problem.  I just went to System --> Admin --> Restricted Drivers Manager and checked the Nvidia box.  My desktop effects didn't work right away, so I copied  over my old xorg.conf from pre-upgrade, and that took care of that problem.

Let me know if you want to double check any settings/configs with what I've got.

---

### Post by sirgrim on 2007-10-18
I'm having these same issues. I think the nvidia-glx files are getting corrupted by packet loss. Try re-installing nvidia-glx, let me know if you get an error.

---

### Post by dweez on 2007-10-19
I get the same error.  Tried installing both -glx and -glx-new with the same results.  I now see that there seems to be a conflict with a libgl* file but I still don't know what I should do to resolve this.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4493kB of archives.
After unpacking 13.7MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted nvidia-glx 1:1.0.9639+2.6.22.4-14.9 [4493kB]
Fetched 4493kB in 12s (365kB/s)                                                
(Reading database ... 152063 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nvidia-kernel-source
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4493kB of archives.
After unpacking 13.7MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted nvidia-glx 1:1.0.9639+2.6.22.4-14.9 [4493kB]
Fetched 4493kB in 12s (365kB/s)                                                
(Reading database ... 152063 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by eosyn on 2007-10-19
I get the same error here too :(

---

### Post by neuralnet on 2007-10-21
Yep, same errors here too.. Nvidia 7600 GS, XP3200+

---

### Post by solinent on 2007-10-22
Yeah, same problems here.  I haven't restarted yet, but it is still upgrading.  Got here through google.  Will edit later when I restart.

---

### Post by dweez on 2007-10-24
I haven't did much testing on this since shortly after my last post.  One of my google searches turned up someone who said that they just kept trying the driver install and it eventually worked.  That's not the case for me.

I might just download the disk and do a fresh install and see what happens.

---

### Post by yazo on 2007-10-25
I have the same problems. I've upgraded a Dell D820 (with nvidia quadro nvs 120M) from 7.04 to 7.10.
After running 
# sudo dpkg-reconfigure xserver-xorg
The maximum I can get is a high resolution view on the laptop screen.
I can't switch to an external screen. 
I can't use the 3d acceleration.

I've been looking for a solution for several hours.

Enabling the nvidia restricted driver causes a 800x600 resolution after startup.
I've tried replacing  nvidia-glx with nvidia-glx-new, which didn't make any difference.

---

### Post by dweez on 2007-10-25
Well, you're a little farther than I.  We have the same laptop but if I try to enable the restricted drivers, I get the previously stated error message.

#1 ADD:
Well, I went ahead and moved all my data off and did clean install and now my restricted drivers worked fine.  Guess the error during the upgrade left some package in a corrupted state that Synaptic/Update Manager couldn't deal with.  I was dual booting so saving my data was as simple as moving it to the Vista partition.  Now I get to reboot into Vista to see if I have to fix the bootloader.  Previous OS installs messed up the bootloader for the previously installed OS (Had XP, installed Ubuntu, had to fix bootload; Then upgraded XP to Vista, had to fix bootloader).  This time, I only deleted the Linux file and left /boot alone and it seemed to do fine.  I'll edit this post again later to let everyone who cares know if it was alright or not.

#2 ADD:
Both grub and the Vista bootloader were left intact by the clean install of Ubuntu 7.10 (well, grub was reinstalled with the clean install) and I am now a happy camper in every way except for the fact that I didn't figure out the real solution to the issue here, just blew it all away and started fresh.

---

### Post by yazo on 2007-10-25
I'll be grateful if you put on the thread your /etc/X11/xorg.conf file. If that doesn't help I'll go on the fresh install option too.

---

### Post by dweez on 2007-10-26
yazo, I'll upload it tomorrow if that is ok.  I typically leave my laptop at work during the week.

---

### Post by mikec13 on 2007-10-26
> **yazo said:**
> I'll be grateful if you put on the thread your /etc/X11/xorg.conf file. If that doesn't help I'll go on the fresh install option too.
Here is my xorg.conf file I use when I'm not using an external monitor.  I've got a little script that switches between this one and another one when I'm going to plug in.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"0"
	Option		"MinSpeed"		".7"
	Option		"MaxSpeed"		"3"
	Option		"AccelFactor"		"0.025"
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
	Identifier	"nVidia Corporation G72M [GeForce Go 7400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-96
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [GeForce Go 7400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1920x1200"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by davekayll on 2007-11-01
**This post could be related to an Ubuntu bug filed at**: i did the upgrade to gutsy and i have the same problem  800*600 max video card ASUS EN7600GS SILENT lets know if you fix [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **yazo said:**
> I have the same problems. I've upgraded a Dell D820 (with nvidia quadro nvs 120M) from 7.04 to 7.10.
After running 
# sudo dpkg-reconfigure xserver-xorg
The maximum I can get is a high resolution view on the laptop screen.
I can't switch to an external screen. 
I can't use the 3d acceleration.

I've been looking for a solution for several hours.

Enabling the nvidia restricted driver causes a 800x600 resolution after startup.
I've tried replacing  nvidia-glx with nvidia-glx-new, which didn't make any difference.

  i

---

