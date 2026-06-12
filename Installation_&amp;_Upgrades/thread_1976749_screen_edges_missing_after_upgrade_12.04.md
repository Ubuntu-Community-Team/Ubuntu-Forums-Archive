---
title: "screen edges missing after upgrade 12.04"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by mooz123 on 2012-05-09
Hi,

I upgraded many times without any display problems, but I just upgraded from 11.10 to 12.04 and it went wrong.
The monitor only shows the middle of the screen, so all the icons to the left are missing, also the account names on the login screen, and the Unity toolbar. The toolbar on top of the screen still shows, except the left and right parts of it, but the top of the desktop is cut off. The mouse works even offscreen, so I can try to guess where a button is and click it to make it work.
What to do?

thanks in advance, Mark

EDIT:
I accidentally opened a JAVA game, and after this the screen was almost like before.
exception: the Unity toolbar is permanently visible

---

### Post by mooz123 on 2012-05-12
Clean install? It seems nobody recognises this... :(

---

### Post by jadtech on 2012-05-12
have you tried a few basic things  creating a new user account to see if  the display changes to normal, log in using ubuntu 2d , reinstalling the video driver ..

go to the terminal type these 

```
sudo apt-get update

sudo apt-get upgrade -f

configure -a


```

others most likely would be able to help as well if you gave more info about  your computer  like  what type of video card, memory,  processor, was there any noted warnings or issues during the upgrade ..

---

### Post by mooz123 on 2012-05-13
Thank you Jadtech, with my Java-game-detour I could do my homework,
Here are my current details:

Memory 2.0 GiB
Processor Intel Core 2 Duo CPU E4500 @ 2.20 GHz x 2
Graphics GeForce GT 220/PCIe/SSE2
OS type 32-bit
HP Pavillion, dual Boot
Precise Pangolin, updated from 11.10

NVIDIA  accelerated graphics driver (post-release update)
screen HP w22 1680x1050

There were no problems during the update.


I tried a couple of things:
-changed to post-release update driver
-created new user account
-updated the system
-entered jadtechs code:
      sudo apt-get update

      sudo apt-get upgrade -f

      configure -a

configure -a gave message: configure: command not found


The problem remains: the monitor is zoomed in on the middle of the screen, the edges are invisible but present (mouse and buttons work). It occurs already between boot and login, and shows in the loginscreen and in all users that I tried.

Does anybody know a fix?

Thanks in advance, Mark

---

### Post by mooz123 on 2012-05-21
Is there an error in xorg.conf?
my xorg.conf:

Section "Monitor"
	Identifier     "Generic Monitor"
	HorizSync       30.0 - 70.0
	VertRefresh     50.0 - 160.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "nVidia Corporation G80 [GeForce 8400 GS]"
	Monitor        "Generic Monitor"
	DefaultDepth    24
	Option         "AddARGBVisuals" "True"
	Option         "AddARGBGLXVisuals" "True"
	Option         "NoLogo" "True"
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	# commented out by update-manager, HAL is now used
	#	Inputdevice	"Generic Keyboard"
	# commented out by update-manager, HAL is now used
	#	Inputdevice	"Configured Mouse"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Keyboard0" "CoreKeyboard"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Mouse0" "CorePointer"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Keyboard0" "CoreKeyboard"
	# commented out by update-manager, HAL is now used and auto-detects devices
	# Keyboard settings are now read from /etc/default/console-setup
	#    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "nVidia Corporation G80 [GeForce 8400 GS]"
	Driver         "nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by mooz123 on 2012-10-22
Problem solved. Last week there was an update ( nvidia-* ) after this the screen was normal again.

---

