---
title: "Dealing with problems with the Xserver"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by tseliot on 2006-06-02
If the Xserver crashes at boot, then this quick fix might do the trick for you.

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Make sure that everything went fine during the update:
```
dpkg --configure -a
```

3) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

4) Reconfigure the login manager:
```
dpkg-reconfigure gdm (if you use Ubuntu or Xubuntu)
```
or
```
dpkg-reconfigure kdm (if you use Kubuntu)
```

and select your desired login manager (either gdm or kdm, according to the version of Ubuntu you're using or to your personal preference)

5) Restart your computer:
```
reboot
```

Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga".

**[COLOR="Red"]NOTE: if you're using a VIA graphic card try this:[/COLOR]**
```
apt-get install xserver-xorg-driver-via
```
then
```
dpkg-reconfigure xserver-xorg
```
and select your Via card (and driver)

P.S. After you're able to use the Desktop Environment I suggest you to install the right drivers for your graphic card in order to make the most of it.


**IF you have an ASUS P5VDC-MX motherboard + onboard VIA**
sudo nano -w /boot/grub/menu.lst

Look for a line which begins with "kopt":
```
# kopt=root=/dev/hdc1 ro
```

and add "pci=conf1" on that line:
```
# kopt=root=/dev/hdc1 ro pci=conf1
```

CTRL+X to exit (save the file)

Then type:
```
sudo update-grub
```

and reboot.

Now the xserver should work fine.

---

### Post by pt123 on 2006-06-02
Thats pretty useless, because if you had nvidia driver set up before in the xorg.conf files you have settings for depth of display and they cause erors when you change it to vga and restart .

These instructions from this thread:
[http://www.ubuntuforums.org/showthread.php?t=185396](http://www.ubuntuforums.org/showthread.php?t=185396)

 help me reconfigure Xserver
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg 
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start

---

### Post by tseliot on 2006-06-03
[QUOTE=pt123]Thats pretty useless, because if you had nvidia driver set up before in the xorg.conf files you have settings for depth of display and they cause erors when you change it to vga and restart .

These instructions from this thread:
[http://www.ubuntuforums.org/showthread.php?t=185396](http://www.ubuntuforums.org/showthread.php?t=185396)

 help me reconfigure Xserver
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg 
sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start[/QUOTE]
I'll put this command instead of that with nano:
```
dpkg-reconfigure xserver-xorg 
```

Notice that I suggest to boot in Recovery mode because sometimes an xserver crash can make the entire computer freeze.

---

### Post by Patrick-Ruff on 2006-06-03
meh, it seems liek the Unable to Mount root error, is much more widespread then that of this, please investigate this thread
[http://ubuntuforums.org/showthread.php?t=186115](http://ubuntuforums.org/showthread.php?t=186115)

---

### Post by Christopher on 2006-06-03
[QUOTE=tseliot]If the Xserver crashes at boot, then this quick fix might do the trick for you.

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

3) Reconfigure the login manager:
```
dpkg-reconfigure gdm (if you use Ubuntu or Xubuntu)
```
or
```
dpkg-reconfigure kdm (if you use Kubuntu)
```

and select your desired login manager (either gdm or kdm, according to the version of Ubuntu you're using or to your personal preference)

4) Restart your computer:
```
reboot
```

Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga".


P.S. After you're able to use the Desktop Environment I suggest you to install the right drivers for your graphic card in order to make the most of it.[/QUOTE]

Ok, I installed Dapper 6.06 with no problems, then proceeded to install nvidia's 8762 driver with no issues. The only problem i had was i wanted my correct resolution which is 1280x1024 @ 85Hz. So i do a **sudo gedit /etc/X11/xorg.conf** and proceed to change my Horz Freq & my Vert Freq according to my monitors manual as i have always done in the past. Then i reboot and i have no GUI im @ a login prompt for username then password, so i enter it and the do a **sudo /etc/init.d/gdm stop** & then i proceed to do a **sudo dpkg-reconfigure xserver-org** and it tells me that Package `xserver-org` is not installed and no info is availible. /usr/sbin/dpkg-reconfigure:xserver-org is not installed. So i now do a **sudo apt-get install xserver-xorg** it says  reading packagelists.....Done, Building dependency tree....Done E:Couldnt find package xserver-org. So i even try a sudo dpkg-reconfigure gdm and i get invoke-rc.d: initscript gdm, action "reload" failed. I then reboot into (recovery mode) and i get all the same issues as listed above,maybe its the nvidia driver 8762? anyone have any ideas? Thank you in advance.

---

### Post by Christopher on 2006-06-03
Anyone?

---

### Post by tseliot on 2006-06-03
[QUOTE=Christopher]Ok, I installed Dapper 6.06 with no problems, then proceeded to install nvidia's 8762 driver with no issues. The only problem i had was i wanted my correct resolution which is 1280x1024 @ 85Hz. So i do a **sudo gedit /etc/X11/xorg.conf** and proceed to change my Horz Freq & my Vert Freq according to my monitors manual as i have always done in the past. Then i reboot and i have no GUI im @ a login prompt for username then password, so i enter it and the do a **sudo /etc/init.d/gdm stop** & then i proceed to do a **sudo dpkg-reconfigure xserver-org** and it tells me that Package `xserver-org` is not installed and no info is availible. /usr/sbin/dpkg-reconfigure:xserver-org is not installed. So i now do a **sudo apt-get install xserver-xorg** it says  reading packagelists.....Done, Building dependency tree....Done E:Couldnt find package xserver-org. So i even try a sudo dpkg-reconfigure gdm and i get invoke-rc.d: initscript gdm, action "reload" failed. I then reboot into (recovery mode) and i get all the same issues as listed above,maybe its the nvidia driver 8762? anyone have any ideas? Thank you in advance.[/QUOTE]
it's sudo dpkg-reconfigure xserver-**x**org

please try again

---

### Post by Christopher on 2006-06-03
[QUOTE=tseliot]it's sudo dpkg-reconfigure xserver-**x**org

please try again[/QUOTE]

Ok, 1st off I apologize for the typo and i typed in sudo dpkg-reconfigure xserver-xorg in recovery mode and got it to work and heres my xorg.conf, can you tell me if it looks ok, thank you in advance.



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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC FE992"
	Option		"DPMS"
	HorizSync	  30-98
	VertRefresh	   50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"NEC FE992"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by kickaha on 2006-06-03
There is a bug # 36461 that's kind of related to this discussion.

It relates to dual-headed operation, where some varying mix of video cards cause the X server to lock up, and take the system with it.

There's no cure, yet.

---

### Post by tseliot on 2006-06-04
[QUOTE=Christopher]Ok, 1st off I apologize for the typo and i typed in sudo dpkg-reconfigure xserver-xorg in recovery mode and got it to work and heres my xorg.conf, can you tell me if it looks ok, thank you in advance.



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

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"NEC FE992"
	Option		"DPMS"
	HorizSync	  30-98
	VertRefresh	   50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"NEC FE992"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection[/QUOTE]
it seems ok. Does it work properly?

---

### Post by Nordoelum on 2006-06-04
I got the GDM to start. But now I have only 640*400. And when I log in, the whole desktop is messed up. I only have a field on the top where I can navigate my mouse pointer.

Any ideas?

---

### Post by tseliot on 2006-06-04
[QUOTE=Nordoelum]I got the GDM to start. But now I have only 640*400. And when I log in, the whole desktop is messed up. I only have a field on the top where I can navigate my mouse pointer.

Any ideas?[/QUOTE]
1) Can you tell me the model of your graphic card?
2) can you post your /etc/X11/xorg.conf ?

---

### Post by Nordoelum on 2006-06-04
1. Intel i810
2. I don't have the Live CD. I have updated through the command line. Since I allready had Breezy installed om my server.

---

### Post by Zalbor on 2006-06-04
My card is an nvidia geforce fx 5700le. The X server wouldn't start, and I did what you said in the beginning of this thread. VESA made GDM load fine, but as soon as I enter my username and password it restarts (screen goes black, then to a text login, then gdm again asking for my name).

What can I do about this? By the way, I had the nvidia drivers installed before upgrading (but not from the nvidia site, I had used the repositories).

EDIT: SOLVED!!!!

I booted in recovery mode (I suppose you don't have to and can just use sudo) and gave these commands:

```
apt-get install nvidia-glx
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bakdap
nvidia-glx-config enable
```
(The second one was only to backup xorg.conf, in case it went wrong)

It seems nvidia-glx needed to be configured again, which means the first command might not be necessary either.

---

### Post by Christopher on 2006-06-04
[QUOTE=tseliot]it seems ok. Does it work properly?[/QUOTE]


It works great, THANK YOU very much for the help tseliot, appreciate it very much. :mrgreen: ;)

---

### Post by winfree on 2006-06-05
[QUOTE=tseliot]If the Xserver crashes at boot, then this quick fix might do the trick for you.

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Make sure that everything went fine during the update:
```
dpkg --configure -a
```

3) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

4) Reconfigure the login manager:
```
dpkg-reconfigure gdm (if you use Ubuntu or Xubuntu)
```
or
```
dpkg-reconfigure kdm (if you use Kubuntu)
```

and select your desired login manager (either gdm or kdm, according to the version of Ubuntu you're using or to your personal preference)

5) Restart your computer:
```
reboot
```

Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga".

**[COLOR="Red"]NOTE: if you're using a VIA graphic card try this:[/COLOR]**
```
apt-get install xserver-xorg-driver-via
```
then
```
dpkg-reconfigure xserver-xorg
```
and select your Via card (and driver)

P.S. After you're able to use the Desktop Environment I suggest you to install the right drivers for your graphic card in order to make the most of it.[/QUOTE]


Hi,
I followed instructions above until 3) when I get message:
xserver-org is not installed and no info is available.

Run breeze on nvidia GeForce4 MX 440 with AGP8. No problems since upgraded using upgrade manager.

Any ideas, I've been tryin to fix pc on my own reading different threads. Any ideas? Thanks.

---

### Post by tseliot on 2006-06-05
[QUOTE=winfree]Hi,
I followed instructions above until 3) when I get message:
xserver-org is not installed and no info is available.

Run breeze on nvidia GeForce4 MX 440 with AGP8. No problems since upgraded using upgrade manager.

Any ideas, I've been tryin to fix pc on my own reading different threads. Any ideas? Thanks.[/QUOTE]
It's not xserver-org but xserver-**x**org

It's likely that you mispelled it and the command didn't work. Please try again

---

### Post by winfree on 2006-06-05
Thank you!
I've working on this upgrade since last friday. I'm responding from dapper!, I had to reboot to w2k to get help.
Thanks again.

---

### Post by pjs_flyer on 2006-06-07
Hi

I followed the instructions, and everything seems to work until I get to dpkg-reconfigure gdm, which throws up the error:

invoke-rc.d: initscript gdm, action "reload" failed

If I press on regardless, I get the ubuntu logo, the scrolling messages, then a brief blank screen, the brown background with the little spinny wheel thing, then it freezes.  Any ideas?

I'm using an amilo a1630 laptop (amd64) with an ATI Mobility Radeon 9700 card. Any help greatle appreciated...

---

### Post by tseliot on 2006-06-07
[QUOTE=pjs_flyer]Hi

I followed the instructions, and everything seems to work until I get to dpkg-reconfigure gdm, which throws up the error:

invoke-rc.d: initscript gdm, action "reload" failed

If I press on regardless, I get the ubuntu logo, the scrolling messages, then a brief blank screen, the brown background with the little spinny wheel thing, then it freezes.  Any ideas?

I'm using an amilo a1630 laptop (amd64) with an ATI Mobility Radeon 9700 card. Any help greatle appreciated...[/QUOTE]
Try with:
try with:
```
sudo apt-get -f install
```

and then:
```
sudo dpkg --configure -a
```

---

### Post by pjs_flyer on 2006-06-07
Thanks - will try as soon as I'm back home! Should this work in recovery mode with a network cable plugged in?

---

### Post by tseliot on 2006-06-07
[QUOTE=pjs_flyer]Thanks - will try as soon as I'm back home! Should this work in recovery mode with a network cable plugged in?[/QUOTE]
Yes, sure

---

### Post by tseliot on 2006-06-07
[QUOTE=Nordoelum]1. Intel i810
2. I don't have the Live CD. I have updated through the command line. Since I allready had Breezy installed om my server.[/QUOTE]
Ok, you don't have the livecd but you're able to use the screen and the Desktop Environment, aren't you?

---

### Post by pjs_flyer on 2006-06-07
Didn't work - still can't get in.  I've tried:

sudo apt-get -f install
sudo apt-get -f remove
sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --configure -a

and I still get the error with dpkg-reconfigure gdm, and I can't get past teh spinny wheel when gdm starts up (it still freezes).

What should I try next?

Thanks for your help so far - much appreciated

---

### Post by tseliot on 2006-06-07
[QUOTE=pjs_flyer]Didn't work - still can't get in.  I've tried:

sudo apt-get -f install
sudo apt-get -f remove
sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --configure -a

and I still get the error with dpkg-reconfigure gdm, and I can't get past teh spinny wheel when gdm starts up (it still freezes).

What should I try next?

Thanks for your help so far - much appreciated[/QUOTE]
try with:
```
sudo apt-get install --reinstall gdm
```

---

### Post by tseliot on 2006-06-07
[QUOTE=tseliot]try with:
```
sudo apt-get install --reinstall gdm
```[/QUOTE]

then type this to restart your computer:
```
sudo reboot
```

---

### Post by pjs_flyer on 2006-06-07
Still no joy - at the end of the reinstaill it comes up with the same error message, and on reboot it hangs just before the gdm login screen...

---

### Post by tseliot on 2006-06-07
[QUOTE=pjs_flyer]Still no joy - at the end of the reinstaill it comes up with the same error message, and on reboot it hangs just before the gdm login screen...[/QUOTE]
Weird... I admit that I'm short of ideas, at least for now.

---

### Post by pjs_flyer on 2006-06-07
Could it be a problem with the gdm.conf or gdm.conf-custom files? What do these need to have in them?

Failing that, is there any way to redo the upgrade, or to go back to breezy? Otherwise, any suggestions as to how I can get everything off my home directory and on to another computer (pc or mac), dvd or memory stick?

---

### Post by tseliot on 2006-06-07
[QUOTE=pjs_flyer]Could it be a problem with the gdm.conf or gdm.conf-custom files? What do these need to have in them?

Failing that, is there any way to redo the upgrade, or to go back to breezy? Otherwise, any suggestions as to how I can get everything off my home directory and on to another computer (pc or mac), dvd or memory stick?[/QUOTE]
I have no idea (at the moment). And the fact that I have slept for only 4 hours doesn't help.

BTW why don't you do a fresh installation of Dapper?

---

### Post by pjs_flyer on 2006-06-07
A fresh installation of dapper might be my only option - I just need to work out how to get some files off there first!

Thanks for your help so far - have a good night's sleep!

---

### Post by alexanderkjerulf on 2006-06-08
Please ignore this - I'd been installing from the server CD and not the desktop one.

Yes, I am a fool :o)


I've just installed dapper on a brand new LG laptop, and though the install seemed to work, I only get a text screen when I start Ubuntu.

[QUOTE=tseliot]If the Xserver crashes at boot, then this quick fix might do the trick for you.

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Make sure that everything went fine during the update:
```
dpkg --configure -a
```

3) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

[/QUOTE]

I tried this, but in step 3 ubuntu says that xserver-xorg is not present.

There isn't even an /etc/X11 directory...

Any ideas will be much appreciated!

---

### Post by pjs_flyer on 2006-06-08
I think that doing

$ sudo apt-get install xserver-xorg

should solve this, but looking at other posts to do with dependencies, you might want to try the following catch-alls

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install xserver-xorg x-window-system-core ubuntu-desktop

$ sudo apt-get -f install

$ sudo apt-get update
$ sudo apt-get dist-upgrade

(making sure it&#8217;s dist-upgrade not upgrade)

I think this all depends on you having an internet connection - I'm sure there's an equivalent if you're doing it from a disc, but I don't know what it is...

Having said this, I can't get my install to work, so I might not be the best person to ask!

---

### Post by Dillius on 2006-06-08
I've tried this with both VGA and VESA. With VGA it just throws constant errors akin to those thrown by trying to use the ATI Drivers. When using VESA, two different issues occur. If I use the default values all the way through, my monitor gives an "Out of Range" or "Out of Sync" error, followed by no signal. If I manually enter my monitor's Vertical and Horizontal Sync's, it simply receives no signal at all.

I have:

ATI Radeon X800 GTO
NEC Multisync LCD 1970GX monitor (Mainly DVI, but I've also tried the VGA connector at times)

I'm unable to get ANY kind of display at all. Even the Desktop CD's Safe Graphics Mode just leads to me having no signal to my monitor.

---

### Post by blitzer on 2006-06-08
I have an AIW ATI 8500 DVI video card and can't get desktop to come up unless I use startx in the console.  I did the vesa try and no luck.  Everything works when I log in except 3d graphics but that's not the problem right now just want desktop to launch again :confused: 

Thanks in advance for any help.

P.S.
I have a ps2 5-button optical mouse (GE brand) that I would really like to use.  I'm using a roller ball mouse now any ideas on how to fix the optical mouse ](*,)

---

### Post by joshua neff on 2006-06-08
I've got a Dell Inspiron 1100. I did a manual upgrade to Dapper on the 1st. Midway through the upgrade, my computer shut off due to the heat in my house. I tried to do the upgrade again, and again the computer shut down. We're running the AC now, so once again, I booted the computer up, did "sudo apt-get update" followed by "sudo apt-get upgrade". This time, it went all the way through the upgrade (at least, that's how it seems). Now, everytime I've rebooted the computer after the attempted upgrades, xserver has crashed. It did it again just now. I followed the instructions on the first post in this thread. Rebooted. Still it crashed. I did it all again, this time choosing "vga" instead of "vesa". Rebooted the computer. Absolute same result--xserver crashed.

Is there anything else I can do? I mean, besides a clean install of Dapper? (And if I have to do a clean install, how do I recover all of the files I saved on my laptop before I do the clean install?)

Man, this is monumentally frustrating.

---

### Post by pjs_flyer on 2006-06-09
Some news on my "issues"...going back a kernel gets me a lot of the way there.  If I hit "escape" on startup and choose the 3rd option on the list, I can boot up - although a few things (e.g. wireless) don't work...however, I am at least in!

---

### Post by tseliot on 2006-06-09
[QUOTE=alexanderkjerulf]Please ignore this - I'd been installing from the server CD and not the desktop one.

Yes, I am a fool :o)


I've just installed dapper on a brand new LG laptop, and though the install seemed to work, I only get a text screen when I start Ubuntu.



I tried this, but in step 3 ubuntu says that xserver-xorg is not present.

There isn't even an /etc/X11 directory...

Any ideas will be much appreciated![/QUOTE]
Try with:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by tseliot on 2006-06-09
[QUOTE=blitzer]I have an AIW ATI 8500 DVI video card and can't get desktop to come up unless I use startx in the console.  I did the vesa try and no luck.  Everything works when I log in except 3d graphics but that's not the problem right now just want desktop to launch again :confused: 

Thanks in advance for any help.

P.S.
I have a ps2 5-button optical mouse (GE brand) that I would really like to use.  I'm using a roller ball mouse now any ideas on how to fix the optical mouse ](*,)[/QUOTE]
```
sudo dkpg-reconfigure gdm
```

reboot and tell me what happens

---

### Post by tseliot on 2006-06-09
[QUOTE=Dillius]I've tried this with both VGA and VESA. With VGA it just throws constant errors akin to those thrown by trying to use the ATI Drivers. When using VESA, two different issues occur. If I use the default values all the way through, my monitor gives an "Out of Range" or "Out of Sync" error, followed by no signal. If I manually enter my monitor's Vertical and Horizontal Sync's, it simply receives no signal at all.

I have:

ATI Radeon X800 GTO
NEC Multisync LCD 1970GX monitor (Mainly DVI, but I've also tried the VGA connector at times)

I'm unable to get ANY kind of display at all. Even the Desktop CD's Safe Graphics Mode just leads to me having no signal to my monitor.[/QUOTE]
Did you upgrade from Breezy or is it a fresh installation of Dapper?

---

### Post by tseliot on 2006-06-09
[QUOTE=joshua neff]I've got a Dell Inspiron 1100. I did a manual upgrade to Dapper on the 1st. Midway through the upgrade, my computer shut off due to the heat in my house. I tried to do the upgrade again, and again the computer shut down. We're running the AC now, so once again, I booted the computer up, did "sudo apt-get update" followed by "sudo apt-get upgrade". This time, it went all the way through the upgrade (at least, that's how it seems). Now, everytime I've rebooted the computer after the attempted upgrades, xserver has crashed. It did it again just now. I followed the instructions on the first post in this thread. Rebooted. Still it crashed. I did it all again, this time choosing "vga" instead of "vesa". Rebooted the computer. Absolute same result--xserver crashed.

Is there anything else I can do? I mean, besides a clean install of Dapper? (And if I have to do a clean install, how do I recover all of the files I saved on my laptop before I do the clean install?)

Man, this is monumentally frustrating.[/QUOTE]
Try with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then:
```
sudo /etc/init.d/gdm restart
```

---

### Post by Efialtis on 2006-06-09
[QUOTE=Dillius]I've tried this with both VGA and VESA. With VGA it just throws constant errors akin to those thrown by trying to use the ATI Drivers. When using VESA, two different issues occur. If I use the default values all the way through, my monitor gives an "Out of Range" or "Out of Sync" error, followed by no signal. If I manually enter my monitor's Vertical and Horizontal Sync's, it simply receives no signal at all.

I have:

ATI Radeon X800 GTO
NEC Multisync LCD 1970GX monitor (Mainly DVI, but I've also tried the VGA connector at times)

I'm unable to get ANY kind of display at all. Even the Desktop CD's Safe Graphics Mode just leads to me having no signal to my monitor.[/QUOTE]

I have the exact same problem with my X800XL and Dell 1905FP connected via DVI. The screens seems to be receiving no signal at all. I'm trying to do a clean install with Dapper-64bit. In the previous version i could use vesa and complete the installation but not any more. Any tips will be appreciated.

---

### Post by tseliot on 2006-06-09
[QUOTE=Efialtis]I have the exact same problem with my X800XL and Dell 1905FP connected via DVI. The screens seems to be receiving no signal at all. I'm trying to do a clean install with Dapper-64bit. In the previous version i could use vesa and complete the installation but not any more. Any tips will be appreciated.[/QUOTE]
Download the alternate-install cd of Dapper instead of the desktop version. In this way you will be able to use the same installer as the one in Breezy

---

### Post by blitzer on 2006-06-09
[QUOTE=tseliot]```
sudo dkpg-reconfigure gdm
```

reboot and tell me what happens[/QUOTE]

Hello tseliot,

Thank you for your reply to everyone's post =D>  you are truly an asset to this community again,[COLOR="Red"] THANK YOU tseliot ![/COLOR]

I stumbled upon the Synaptic Package managers (4)button features at the bottom left of the window.   I clicked on the button [COLOR="Blue"]CUSTOM [/COLOR] and it gives you a list of the problems on your unbuntu.  That's where I saw my gdm desktop in the list so I did the select for reinstallation.  My GUI login is back !  

My mouse problem is resolved by using a different (Swapped mine for my sons) optical mouse and Ubuntu is using the Micro Innovations (Wal-Mart) mouse with no problems. :D 

Any ideas on getting my ATI Video card 3D for gaming installed without breaking Ubuntu again ? [-o<

---

### Post by joshua neff on 2006-06-09
First, let me also thank you, tseliot, for your patience with everyone in this thread and all of your help.

Second, I just tried this--

[QUOTE=tseliot]Try with:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then:
```
sudo /etc/init.d/gdm restart
```[/QUOTE]

--as per your suggestion. I rebooted and got the exact same xserver crash as I've been getting.

Rats.

---

### Post by tseliot on 2006-06-10
[QUOTE=blitzer]Any ideas on getting my ATI Video card 3D for gaming installed without breaking Ubuntu again ? [-o<[/QUOTE]
I use Nvidia cards. I suggest you to use the search function to find a good guide about the ATI driver.

Or try this:
[http://doc.gwos.org/index.php/3D_Graphic_Cards_Dapper]("http://doc.gwos.org/index.php/3D_Graphic_Cards_Dapper")
OR
[http://doc.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("http://doc.ubuntu.com/ubuntu/desktopguide/C/hardware.html")

---

### Post by tseliot on 2006-06-10
[QUOTE=joshua neff]First, let me also thank you, tseliot, for your patience with everyone in this thread and all of your help.

Second, I just tried this--



--as per your suggestion. I rebooted and got the exact same xserver crash as I've been getting.

Rats.[/QUOTE]
See if anything went wrong:
```
sudo apt-get install -f
```

---

### Post by joshua neff on 2006-06-10
[QUOTE=tseliot]See if anything went wrong:
```
sudo apt-get install -f
```[/QUOTE]

Okay, this is what came up after I did that:

> 
Reading package lists... Done.
Building dependency tree... Done.
0 upgraded, 0 newly installed, 0 to remove and 365 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hplip-base (0.9.5-2ubuntu2)...
Creating/updating hplip user account...
* Starting HP Linux Printing and Imaging System   [ok]

And then it brought the command line cursor back.

---

### Post by joshua neff on 2006-06-10
After that last post, I redid

> apt-get upgrade

and then tried everything again. It still didn't work, but I did figure out at least part of the problem: the kernel hasn't upgraded. I'm going to start a new thread about this.

---

### Post by tseliot on 2006-06-10
[QUOTE=joshua neff]After that last post, I redid



and then tried everything again. It still didn't work, but I did figure out at least part of the problem: the kernel hasn't upgraded. I'm going to start a new thread about this.[/QUOTE]
Can you type this command and post its output?
```
uname -r
```

---

### Post by jørgen on 2006-06-10
I have just installed dapper drake 64bit from the alternative install cd.(the other one just crashed when the x-server started) When the X-server is starting the computer turns off.

I have tried both vga and vesa, but they don't work. The laptop turns off when the X-server is starting. I have ati mobility radeon 9600\9700. And an AMD Athlon 64 prosessor.

---

### Post by joshua neff on 2006-06-10
[QUOTE=tseliot]Can you type this command and post its output?
```
uname -r
```[/QUOTE]

Sure. It said:

> 2.6.12-9-386

---

### Post by tseliot on 2006-06-10
[QUOTE=joshua neff]Sure. It said:[/QUOTE]
1) Try this command:
```
sudo apt-get install linux-386
```

2) Reboot

3) Post the output of uname -r again.

---

### Post by tseliot on 2006-06-10
[QUOTE=jørgen]I have just installed dapper drake 64bit from the alternative install cd.(the other one just crashed when the x-server started) When the X-server is starting the computer turns off.

I have tried both vga and vesa, but they don't work. The laptop turns off when the X-server is starting. I have ati mobility radeon 9600\9700. And an AMD Athlon 64 prosessor.[/QUOTE]
Weird. You might try disabling ACPI but I guess that would mean crippling you laptop.

Just a question: why did you install Ubuntu 64bit instead of Ubuntu 32bit?

---

### Post by joshua neff on 2006-06-10
[QUOTE=tseliot]1) Try this command:
```
sudo apt-get install linux-386
```

2) Reboot

3) Post the output of uname -r again.[/QUOTE]

Okay. I typed:

> sudo apt-get install linux-386

--and it said "newest version of linux-386 is already installed." But then I saw in the list of packages it was holding back something called *linux-image-386*. So, I went ahead and typed:

> sudo apt-get install linux-image-386

--then rebooted. This time it actually went through the whole load up successfully, but then xserver still crashed. *sigh* But I typed:

> uname -r

--and it now says "2.6.15-23-306."

---

### Post by joshua neff on 2006-06-10
Okay, so after the kernel updated, I went ahead and tried your earlier suggestion ("apt-get reconfigure -phigh xserver-xorg" then "apt-get /etc/init.d/gdm restart"). And it worked!

Sort of. My monitor now has the tiny screen-within-a-screen look. I remember this was a problem when upgrading to Breezy, too. But I don't recall how you fix it.

EDIT: Okay, thanks to [this thread](http://www.ubuntuforums.org/showthread.php?t=190022), I've got everything up and running as it should be.

Thanks again, tseliot. You were a huge help.

---

### Post by jørgen on 2006-06-10
[QUOTE=tseliot]Weird. You might try disabling ACPI but I guess that would mean crippling you laptop.

Just a question: why did you install Ubuntu 64bit instead of Ubuntu 32bit?[/QUOTE]

Shouldn't I? I have athlon 64 prosessor, i thought i had to install 64 bit. 

Should i try 32 bit?

---

### Post by tseliot on 2006-06-11
[QUOTE=jørgen]Shouldn't I? I have athlon 64 prosessor, i thought i had to install 64 bit. 

Should i try 32 bit?[/QUOTE]
You suggest you to try Ubuntu 32bit. I'm convinced that if you need to use Ubuntu on the desktop Ubuntu 64 bit will only make your life harder.

---

### Post by jørgen on 2006-06-11
[QUOTE=tseliot]You suggest you to try Ubuntu 32bit. I'm convinced that if you need to use Ubuntu on the desktop Ubuntu 64 bit will only make your life harder.[/QUOTE]

The x-server crashes anyway... I have a Fujitsu Siemens Amilo A 1630, same as someone else in this thread. Looks like he have the same problem.

---

### Post by andyccn on 2006-06-11
Hi, been reading through all the problems, and have found some similar to mine, but cannot work out if they're the same issue.

I've just installed a fresh copy of the Dapper alternate (32-bit) install.  This is on an Athlon-64 3700+, 1GB RAM, Seagate SCSI drives (RAID-1.)

It runs through the entire boot-up fine, displaying the graphical scrolling list of what's loading, then at the point it's supposed to bring up the login screen, I just get a blank screen.  The monitor/signal etc stays on OK, but it's all black.

I tried the procedure in the first post of this topic, but it didn't change anything.  The graphics card is an on-board 32MB S3 Unichrome chip on a VIA chipset.

This also happened on the 64-bit install - I've had Breezy, and Fedora 5 on this machine before.  Gonna try Breezy again now to make sure the machine's OK.

Any suggestions would be appreciated!  Thanks, Andy

---

### Post by Dillius on 2006-06-11
[QUOTE=tseliot]Did you upgrade from Breezy or is it a fresh installation of Dapper?[/QUOTE]
Fresh Install.

At this point i've used the alternative CD to successfully install it onto the computer, but the problem remains that if I try to boot in Safe Graphics mode from the Live CD OR i try booting from my actual install with vesa or vga drivers, i have NO display at all. I can hear the sounds of it starting up successfully, I just have no signal to my screen at all.

---

### Post by andyccn on 2006-06-11
[QUOTE=Dillius]Fresh Install.

At this point i've used the alternative CD to successfully install it onto the computer, but the problem remains that if I try to boot in Safe Graphics mode from the Live CD OR i try booting from my actual install with vesa or vga drivers, i have NO display at all. I can hear the sounds of it starting up successfully, I just have no signal to my screen at all.[/QUOTE]

This sounds about like mine.  I've just finished a normal install of Breezy on the same machine - sweet as a nut, display, resolutions - everything's fine.  Just Dapper that refuses to show the display after boot-up.

---

### Post by jørgen on 2006-06-11
Looks like many people have problems with dapper. Were it many problems with the other Ubuntu releases, or is Dapper unique?

---

### Post by primozs on 2006-06-11
[QUOTE=jørgen]Looks like many people have problems with dapper. Were it many problems with the other Ubuntu releases, or is Dapper unique?[/QUOTE]

Hello my first post dont know where else to put it.

Have problem like this...
Can't log in after upgrade from Ubuntu 5.1 to Ubuntu 6.06
Ubuntu freezes after login screen


i could not log in as normal user to xserver
it seamed like  X-Server is broken so i tried dpkg-reconfigure xserver-xorg;

i also got something like this as root
root@neo:~# gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 5 of 5.
  Command failed 5 times, aborting.
Kon het configuratiebestand van GDM niet benaderen.
root@neo:~#

so i tried repairing /etc/gdm/gdm.conf
i try ed removing the files ~/.Xauthority and ~/.ICEauthority from homedir

in the end it was just no disk space on root partition
check this first.

In general two days ago i was getting a lot of random crashes of xserver. Don't know why. If this helps somebody i am glad.

---

### Post by waltervalderrama on 2006-06-11
Hi. Had the same problem, x server could not start. I tried

sudo apt-get install nvidia-glx
nvidia-glx-config enable
sudo dpkg-reconfigure gdm

Booted the system again and x server started. The only problem is that i have a keyboard conflict. It seems that my keyboard is properly configured in xorg.conf but not in gdm. how can i get this configuration work in gdm?. When i try to log in gdm i type my username and i see strange characters. I cannot log in gdm. I have a "la" keyboard configuration, and it is not working in gdm but with xkb.

Any ideas????????

---

### Post by Alcibiades Mystery on 2006-06-11
THANKS!!! This worked great for me, with only one minor problem. I had previously been using a 1280X1024 resolution, and now I only have the option of 1024X768, 800X600, and 640X480. Is there any way that I can go in and get a 1280X1024 resolution, or do I have to do it all again and select something different on the XServer configuration?

---

### Post by tibro on 2006-06-12
hi!
I have problems with x server too.
I've just installed ubuntu dapper drake amd64 alternate version, but i cannot start x server. 
Xorg.0.log says
(II) ati: Candidate "Device" section "ATI Technologies, Inc. R423 5F57 [RADEON X800XT (PCIE)]"
(WW) ati: pci mach64 in slot 1:0:0 could not be detected
(WW) ati: pci mach64 in slot 1:0:1 could not be detected
(EE) no device detected

fatal server error:
no screens found
what should i do now?
i tried the "vesa" driver and i got blank screen :(
Please help me

---

### Post by Dillius on 2006-06-12
[QUOTE=tibro]hi!
I have problems with x server too.
I've just installed ubuntu dapper drake amd64 alternate version, but i cannot start x server. 
Xorg.0.log says
(II) ati: Candidate "Device" section "ATI Technologies, Inc. R423 5F57 [RADEON X800XT (PCIE)]"
(WW) ati: pci mach64 in slot 1:0:0 could not be detected
(WW) ati: pci mach64 in slot 1:0:1 could not be detected
(EE) no device detected

fatal server error:
no screens found
what should i do now?
i tried the "vesa" driver and i got blank screen :(
Please help me[/QUOTE]

Been trying to find a solution for like 3 days... nothing. Looks like a lot of us are going to be waiting on 6.10.

---

### Post by tseliot on 2006-06-12
[QUOTE=jørgen]The x-server crashes anyway... I have a Fujitsu Siemens Amilo A 1630, same as someone else in this thread. Looks like he have the same problem.[/QUOTE]
1) Did you try "vga" driver instead of "vesa"?

2) If you already did you can try installing ATI's proprietary driver:
```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Make sure you use a ` instead of a '

then:
```
sudo dpkg-reconfigure xserver-xorg
```

and select "fglrx" driver

---

### Post by tseliot on 2006-06-12
[QUOTE=andyccn]I tried the procedure in the first post of this topic, but it didn't change anything.  The graphics card is an on-board 32MB S3 Unichrome chip on a VIA chipset.

This also happened on the 64-bit install - I've had Breezy, and Fedora 5 on this machine before.  Gonna try Breezy again now to make sure the machine's OK.

Any suggestions would be appreciated!  Thanks, Andy[/QUOTE]
Did you try also the part about VIa cards?

---

### Post by tseliot on 2006-06-12
[QUOTE=Dillius]Fresh Install.

At this point i've used the alternative CD to successfully install it onto the computer, but the problem remains that if I try to boot in Safe Graphics mode from the Live CD OR i try booting from my actual install with vesa or vga drivers, i have NO display at all. I can hear the sounds of it starting up successfully, I just have no signal to my screen at all.[/QUOTE]
try installing ATI's proprietary driver:
```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Make sure you use a ` instead of a '

then:
```
sudo dpkg-reconfigure xserver-xorg
```

and select "fglrx" driver

---

### Post by tseliot on 2006-06-12
[QUOTE=primozs]Hello my first post dont know where else to put it.

Have problem like this...
Can't log in after upgrade from Ubuntu 5.1 to Ubuntu 6.06
Ubuntu freezes after login screen


i could not log in as normal user to xserver
it seamed like  X-Server is broken so i tried dpkg-reconfigure xserver-xorg;

i also got something like this as root
root@neo:~# gdmsetup
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again. Try 5 of 5.
  Command failed 5 times, aborting.
Kon het configuratiebestand van GDM niet benaderen.
root@neo:~#

so i tried repairing /etc/gdm/gdm.conf
i try ed removing the files ~/.Xauthority and ~/.ICEauthority from homedir

in the end it was just no disk space on root partition
check this first.

In general two days ago i was getting a lot of random crashes of xserver. Don't know why. If this helps somebody i am glad.[/QUOTE]
What's the model of your graphic card?

---

### Post by tseliot on 2006-06-12
[QUOTE=Alcibiades Mystery]THANKS!!! This worked great for me, with only one minor problem. I had previously been using a 1280X1024 resolution, and now I only have the option of 1024X768, 800X600, and 640X480. Is there any way that I can go in and get a 1280X1024 resolution, or do I have to do it all again and select something different on the XServer configuration?[/QUOTE]
Try with:
```
sudo dpkg-reconfigure xserver-xorg
```

and when it asks you about your monitor select "advanced". Set the horizontal and vertical refresh rate and resolution.

---

### Post by tseliot on 2006-06-12
[QUOTE=tibro]hi!
I have problems with x server too.
I've just installed ubuntu dapper drake amd64 alternate version, but i cannot start x server. 
Xorg.0.log says
(II) ati: Candidate "Device" section "ATI Technologies, Inc. R423 5F57 [RADEON X800XT (PCIE)]"
(WW) ati: pci mach64 in slot 1:0:0 could not be detected
(WW) ati: pci mach64 in slot 1:0:1 could not be detected
(EE) no device detected

fatal server error:
no screens found
what should i do now?
i tried the "vesa" driver and i got blank screen :(
Please help me[/QUOTE]
try installing ATI's proprietary driver:
```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Make sure you use a ` instead of a '

then:
```
sudo dpkg-reconfigure xserver-xorg
```

and select "fglrx" driver

---

### Post by tseliot on 2006-06-12
[QUOTE=waltervalderrama]Hi. Had the same problem, x server could not start. I tried

sudo apt-get install nvidia-glx
nvidia-glx-config enable
sudo dpkg-reconfigure gdm

Booted the system again and x server started. The only problem is that i have a keyboard conflict. It seems that my keyboard is properly configured in xorg.conf but not in gdm. how can i get this configuration work in gdm?. When i try to log in gdm i type my username and i see strange characters. I cannot log in gdm. I have a "la" keyboard configuration, and it is not working in gdm but with xkb.

Any ideas????????[/QUOTE]
Try with:
```
sudo dpkg-reconfigure xserver-xorg
```

and choose your keyboard

---

### Post by Dillius on 2006-06-12
[QUOTE=tseliot]try installing ATI's proprietary driver:
```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Make sure you use a ` instead of a '

then:
```
sudo dpkg-reconfigure xserver-xorg
```

and select "fglrx" driver[/QUOTE]

E: Couldn't find package xorg-driver-fglrx

EDIT: I'm an idiot. Hanlded it.

---

### Post by jørgen on 2006-06-12
[QUOTE=tseliot]1) Did you try "vga" driver instead of "vesa"?

2) If you already did you can try installing ATI's proprietary driver:
```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Make sure you use a ` instead of a '

then:
```
sudo dpkg-reconfigure xserver-xorg
```:-( 
Been there, done that! Stil no change

---

### Post by tseliot on 2006-06-13
[QUOTE=jørgen][QUOTE=tseliot]1) Did you try "vga" driver instead of "vesa"?

2) If you already did you can try installing ATI's proprietary driver:
```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Make sure you use a ` instead of a '

then:
```
sudo dpkg-reconfigure xserver-xorg
```:-( 
Been there, done that! Stil no change[/QUOTE]
Did you try any other distribution with success?

Try Knoppix 5.0.1 which is a live distro and see if it works for you.

It has a different kernel from the one in Ubuntu.

(And BTW you can install it to your hard disk if you want)

If even Knoppix doesn't support your card then I wouldn't know what to suggest...

---

### Post by jørgen on 2006-06-13
I have tried the SUSE 10 live cd, it starts and everything is fine. But some minutes later the computer turns itself off.

[QUOTE=tseliot][QUOTE=jørgen]
Did you try any other distribution with success?

Try Knoppix 5.0.1 which is a live distro and see if it works for you.

It has a different kernel from the one in Ubuntu.

(And BTW you can install it to your hard disk if you want)

If even Knoppix doesn't support your card then I wouldn't know what to suggest...[/QUOTE]

---

### Post by tseliot on 2006-06-13
It is likely that your hardware is not fully compatible with Linux kernel 2.6.15.x

Try disabling ACPI and/or APIC from the bios.

If you can't, you should try Knoppix and see if you have the same problem.

Knoppix uses kernel 2.6.17. Perhaps your motherboard is supported by that version of the kernel.

If even that does not work and you want to use an alternative to Windows you can try Desktop-BSD or PC-BSD (they are both based on FreeBSD).

---

### Post by hal8000 on 2006-06-15
Where are the mode lines for the graphics card? In other distros (non-debian based)
there are always mode lines which you can manually define with xmode or xmodelines.

Luckily my display is working fine so far, but Im curious as to why there are no modelines.
Thanks in advance and this thread is very helpful.

---

### Post by tseliot on 2006-06-15
[QUOTE=hal8000]Where are the mode lines for the graphics card? In other distros (non-debian based)
there are always mode lines which you can manually define with xmode or xmodelines.

Luckily my display is working fine so far, but Im curious as to why there are no modelines.
Thanks in advance and this thread is very helpful.[/QUOTE]
There isn't any in Ubuntu. But you can find a way to set them up by following this guide:
[http://doc.gwos.org/index.php/ChangeResolution]("http://doc.gwos.org/index.php/ChangeResolution")

---

### Post by NutrOn on 2006-06-17
My Dapper upgrade failed, thought I'd post possible errors and see what anybody comes up with. I tried the fix on this forum, however; fail restricted driver/ fail resolver state.
     fail to load module kbd, failed module mouse: no mouse exists-no input driver. no core keyboard. lots of libGL stuff, won't load it. I have an ATI 9550. 
     Can't open kdb, can't open mouse.
     Other log stuff: /etc/rcs.d/S40pcmcia line 139 seg fault 8076. fatal 10 error 104 || connection reset by peer.
     drm open failed. And some bluetooth messages, and no card found messages.
     This may all be unhelpful but here it is.
Any suggestions?
:-( 
Can't open kdb was specific to trying the fix on this thread.
Thanks.
           NutrOn

---

### Post by tseliot on 2006-06-18
[QUOTE=NutrOn]My Dapper upgrade failed, thought I'd post possible errors and see what anybody comes up with. I tried the fix on this forum, however; fail restricted driver/ fail resolver state.
     fail to load module kbd, failed module mouse: no mouse exists-no input driver. no core keyboard. lots of libGL stuff, won't load it. I have an ATI 9550. 
     Can't open kdb, can't open mouse.
     Other log stuff: /etc/rcs.d/S40pcmcia line 139 seg fault 8076. fatal 10 error 104 || connection reset by peer.
     drm open failed. And some bluetooth messages, and no card found messages.
     This may all be unhelpful but here it is.
Any suggestions?
:-( 
Can't open kdb was specific to trying the fix on this thread.
Thanks.
           NutrOn[/QUOTE]
Try with:
sudo apt-get install ubuntu-desktop (or "kubuntu-desktop" if you usr kubuntu)

then:
```
sudo dpkg-reconfigure xserver-xorg
```

and select your mouse and keyboard. (press ENTER when you don't know the answer to the questions.

---

### Post by NutrOn on 2006-06-18
Thanks, I'll give it a try.
NutrOn 
#-o

---

### Post by ezphilosophy on 2006-06-18
First of all, fantastic thread.  Thanks for all the help tseliot.

I just got a new computer and want to do a fresh install of dapper.  I downloaded the 64-bit version but now realize that I will be better off with the 32.  Nevertheless, when I tried to install from CD, when it came to the graphical part of the install, I get a bunch of multi-colored garbage on my screen.  I figured it might be a bad CD.  (For some reason, I have had bad luck in the past trying to burn ISO files in Windows.  Seems they never work.)

I decided to load up breezy since I have a nice printed CD from ship-it.  The install went fine until it came time for GDM to come on and I got the multi-colored mess again.  I found this thread and changed my driver to vesa like you said and it worked fine.

Now, my question is:
As I am downloading the 32-bit version, I'm thinking that I'm probably going to have the same problem as the 64-bit version.  How can I load the vesa driver in advance, before the install?

---

### Post by tseliot on 2006-06-18
[QUOTE=ezphilosophy]First of all, fantastic thread.  Thanks for all the help tseliot.

I just got a new computer and want to do a fresh install of dapper.  I downloaded the 64-bit version but now realize that I will be better off with the 32.  Nevertheless, when I tried to install from CD, when it came to the graphical part of the install, I get a bunch of multi-colored garbage on my screen.  I figured it might be a bad CD.  (For some reason, I have had bad luck in the past trying to burn ISO files in Windows.  Seems they never work.)

I decided to load up breezy since I have a nice printed CD from ship-it.  The install went fine until it came time for GDM to come on and I got the multi-colored mess again.  I found this thread and changed my driver to vesa like you said and it worked fine.

Now, my question is:
As I am downloading the 32-bit version, I'm thinking that I'm probably going to have the same problem as the 64-bit version.  How can I load the vesa driver in advance, before the install?[/QUOTE]
If you're planning to use the live installer you can use the Safe Mode

---

### Post by ezphilosophy on 2006-06-19
[QUOTE=tseliot]If you're planning to use the live installer you can use the Safe Mode[/QUOTE]

Perfect.  Thanks.  Worked without a problem.  Now, I go on to try your Envy script.

How is the Envy script different from the installer in Automatix?  Is one better than the other?  Same?

---

### Post by tseliot on 2006-06-19
[QUOTE=ezphilosophy]Perfect.  Thanks.  Worked without a problem.  Now, I go on to try your Envy script.

How is the Envy script different from the installer in Automatix?  Is one better than the other?  Same?[/QUOTE]
Automatix installs the driver from the repositories (which won't be updated when a new version is out)

Envy can solve driver mismatches (e.g. if you made a mess :p  ) and it will install always the latest driver (I update it regularly) from Nvidia's website.
Envy also supports recompiled kernels but removes the Restricted modules.

BTW Version 0.38 of Envy has just been released. I suggest you to get the latest version.

---

### Post by ezphilosophy on 2006-06-19
I don't see the .38 version on your website, only 0.37.

Also, do you mean that .38 is a stable release?

---

### Post by tseliot on 2006-06-19
[QUOTE=ezphilosophy]I don't see the .38 version on your website, only 0.37.

Also, do you mean that .38 is a stable release?[/QUOTE]
Refresh the page and you will see it

---

### Post by ezphilosophy on 2006-06-20
If I already installed the nvidia drivers from Automatix, and I still wanted to use your script, is that no problem?  So, what I mean is, will your script "undo" or "overwrite" what Automatix did?  
I noticed that automatix did not put the nice "nvidia settings" in my menu.
Maybe it would be just as easy to do that myself.

Also, I can't seem to get into 1280x1024 resolution.

---

### Post by tseliot on 2006-06-20
[QUOTE=ezphilosophy]So, what I mean is, will your script "undo" or "overwrite" what Automatix did?[/QUOTE]
Yes, of course. 

[QUOTE=ezphilosophy]I noticed that automatix did not put the nice "nvidia settings" in my menu.
Maybe it would be just as easy to do that myself.[/QUOTE]
My script does it

[QUOTE=ezphilosophy]Also, I can't seem to get into 1280x1024 resolution.[/QUOTE]
See point 13 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

If that doesn't solve the problem try point 5

---

### Post by ezphilosophy on 2006-06-20
[QUOTE=tseliot]
See point 13 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION")

If that doesn't solve the problem try point 5[/QUOTE]

Wow.  You truly are an asset.

Well, for the record, I'm running a nvidia 6800 GS (256 MB).  (In case that's important.)

When I run the Envy script, would I select (I)nstall or (R)einstall?

---

### Post by tseliot on 2006-06-20
[QUOTE=ezphilosophy]Wow.  You truly are an asset.

Well, for the record, I'm running a nvidia 6800 GS (256 MB).  (In case that's important.)

When I run the Envy script, would I select (I)nstall or (R)einstall?[/QUOTE]
Install

---

### Post by gregb49 on 2006-06-20
[QUOTE=tseliot]If you can't, you should try Knoppix [/QUOTE]Also an obvious trick to experts but maybe not to us mere users, if you can boot your graphics card OK from either your downloaded ubuntu distro or another live CD, but not when you try to install it, then check what xorg settings the CD is using (etc/x11/xorg.conf) Interestingly my EPIA boards will not load Dapper on older and laptop displays but will load from the install CD as the install CD sets up xorg.conf differently. 

I discovered that this device section worked fine (see below), once I had edited the xorg.conf file using a live CD (I use dyne:bolic as it gives access to everything, it seems and also works with more motherboards than most, in my experience). I am now left with a boot up graphics problem in that all my EPIA boards boot with unreadable brown streaks until the login appears, but I can live with that. Greg
-------------------------------------------------------------------------------------
Section "Device"
	Identifier	"VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics"
	Driver		"via"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
-------------------------------------------------------------------------------------

EPIA M10000/5000 Nehemiah 1GHz, 1GB, 80GB 2.5" drive. Ubunutu 6.06

---

### Post by tseliot on 2006-06-20
[QUOTE=gregb49]I am now left with a boot up graphics problem in that all my EPIA boards boot with unreadable brown streaks until the login appears, but I can live with that.[/QUOTE]
Try this:
```
sudo nano -w /boot/grub/menu.lst
```

look for this line: Code: 

```
# defoptions=quiet splash
```

Remove the word "splash" from it. 

Save and exit: press CTRL+X 

Then type this in Terminal or Konsole: Code: 

```
sudo update-grub
```

and restart your computer 

After that, you will have no pretty usplash screen to look at anymore but the bug should be gone.

---

### Post by ezphilosophy on 2006-06-20
tseliot,
First of all, everything worked like a charm.  I ran the envy script and it loaded everything perfectly.  Then, I went on to the "change resolution guide" written by heimo and that also worked beautifully.

The problem came when I tried to get xgl/compiz working.  I worked through this guide [http://www.compiz.net/viewtopic.php?id=652&p=1]("http://www.compiz.net/viewtopic.php?id=652&p=1")

After that, I rebooted and everything looked good.  Then, I noticed that my windows were suddenly acting slow.  I looked at applications>system tools>nvidia settings and it seems that it doesn't recognize my GPU anymore.

I'm not sure if I should be writing this on the other thread, but I just thought you might know the reason/answer and moreover, a fix?

Can I/should I run the envy script again?  I looked at my xorg.conf file and it seems the same as before (except for the changes for xgl/compiz).

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce 6800 GS"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
        Option          "RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"LG L1950SQ"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6800 GS"
	Monitor		"LG L1950SQ"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I'm not sure what my next move should be.

Any ideas?

---

### Post by tseliot on 2006-06-20
[QUOTE=ezphilosophy]tseliot,
First of all, everything worked like a charm.  I ran the envy script and it loaded everything perfectly.  Then, I went on to the "change resolution guide" written by heimo and that also worked beautifully.

The problem came when I tried to get xgl/compiz working.  I worked through this guide [http://www.compiz.net/viewtopic.php?id=652&p=1]("http://www.compiz.net/viewtopic.php?id=652&p=1")

After that, I rebooted and everything looked good.  Then, I noticed that my windows were suddenly acting slow.  I looked at applications>system tools>nvidia settings and it seems that it doesn't recognize my GPU anymore.

I'm not sure if I should be writing this on the other thread, but I just thought you might know the reason/answer and moreover, a fix?

Can I/should I run the envy script again?  I looked at my xorg.conf file and it seems the same as before (except for the changes for xgl/compiz).

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA GeForce 6800 GS"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
        Option          "RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"LG L1950SQ"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA GeForce 6800 GS"
	Monitor		"LG L1950SQ"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I'm not sure what my next move should be.

Any ideas?[/QUOTE]
I don't use XGL because it's not stable yet. Try removing XGL

---

### Post by gregb49 on 2006-06-20
Thanks tseliot, that did the job (removing splash and updating grub)
Greg

---

### Post by Efialtis on 2006-06-21
[QUOTE=Efialtis]I have the exact same problem with my X800XL and Dell 1905FP connected via DVI. The screens seems to be receiving no signal at all. I'm trying to do a clean install with Dapper-64bit. In the previous version i could use vesa and complete the installation but not any more. Any tips will be appreciated.[/QUOTE]

After i found some time to spare on my problem yesterday this is what worked for me and hopefully will work for some of you out there.
First of all i used the i386 desktop CD of Dapper as the AMD64 version wasn't cutting it for me for some strange reason. I did a safe graphics install (using the Vesa driver) and updated my system through update manager. After that i downloaded the latest i386 ATI driver from their site (8.25.18 ) that supports the XOrg 7.0 of Dapper. Followed their instructions for automatic installation on XOrg 7.0 (no package building) and when that finished i reconfigured Xorg to use the fglrx driver, maybe this was overkill but i did it anyway. Killed the X with Ctrl+Alt+Backspace and it worked like a charm :mrgreen: .
Since i'm new to Ubuntu i dont think i would really benefit from the AMD64 version and from what i read its better to go with the i386 as it will save you some trouble down the road (for a novice user like me that is).

---

### Post by ezphilosophy on 2006-06-21
Yeah, stability.....  good point.  

Well, I went through the tutorial backwards at just deleted files and changed the xorg.  I didn't bother to uninstall the compiz files.  I assume that it is no problem them just sitting there.  Am I right?

I rebooted and the nvidia settings appear like they did before.  I hope that is all there is to it.

---

### Post by tseliot on 2006-06-21
[QUOTE=ezphilosophy]Yeah, stability.....  good point.  

Well, I went through the tutorial backwards at just deleted files and changed the xorg.  I didn't bother to uninstall the compiz files.  I assume that it is no problem them just sitting there.  Am I right?

I rebooted and the nvidia settings appear like they did before.  I hope that is all there is to it.[/QUOTE]
If nvidia settings is ok the driver must be ok too

---

### Post by ezphilosophy on 2006-06-22
Excellent.

Another question, are there other ways of achieving window transparency other than using xgl/compiz?  Or maybe just using xgl?  Both unstable?

Better luck in KDE?

---

### Post by PoisoN2003 on 2006-06-22
What do i do if after i upgraded to dapper i reconfigured my xorg because it rashed when booting so now the my nvidia 5600 fx ultra isnt working
tried reinstalling drivers but when i reboot it crashes maybe i have to delete something before i reinstall them??
i tried to use your script and this is what i get hopefully u can help me

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Jun 23 00:41:01 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: true
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/lib/xorg/
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/kernel-headers-2.6.16-ck12
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC test with CC="cc".
-> Using the kernel source path '/usr/src/kernel-headers-2.6.16-ck12' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Kernel output path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/kernel-headers-2.6.
   16-ck12 SYSOUT=/usr/src/kernel-headers-2.6.16-ck12'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/kernel-headers-2.6.16-ck12 SUBDIRS=
   /home/poison/NVIDIA-Linux-x86-1.0-8762-pkg1/usr/src/nv modules
   /usr/src/kernel-headers-2.6.16-ck12/arch/i386/Makefile:38: /usr/src/kernel-h
   eaders-2.6.16-ck12/arch/i386/Makefile.cpu: No such file or directory
   make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.16-ck12/arc
   h/i386/Makefile.cpu'.  Stop.
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by tseliot on 2006-06-24
> **PoisoN2003]What do i do if after i upgraded to dapper i reconfigured my xorg because it rashed when booting so now the my nvidia 5600 fx ultra isnt working
tried reinstalling drivers but when i reboot it crashes maybe i have to delete something before i reinstall them??
i tried to use your script and this is what i get hopefully u can help me

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Jun 23 00:41:01 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: true
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/lib/xorg/
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/kernel-headers-2.6.16-ck12
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC test with CC="cc".
-> Using the kernel source path '/usr/src/kernel-headers-2.6.16-ck12' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Kernel output path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv said:**
> : *** No rule to make target `/usr/src/kernel-headers-2.6.16-ck12/arc
   h/i386/Makefile.cpu'.  Stop.
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```
Try my script and use the "install" function:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by PoisoN2003 on 2006-06-24
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jun 24 15:57:20 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: true
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/lib/xorg/
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/kernel-headers-2.6.16-ck12
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC test with CC="cc".
-> Using the kernel source path '/usr/src/kernel-headers-2.6.16-ck12' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Kernel output path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
   rm -f -f nv.o nv-vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nv.o nv
   -vm.o os-agp.o os-interface.o os-registry.o nv-i2c.o nvidia.mod.o
   rm -f -f build-in.o nv-linux.o *.d .*.{cmd,flags}
   rm -f -f nvidia.{o,ko,mod.{o,c}} nv_compiler.h *~
   rm -f -f stprof stprof.o symtab.h
   rm -f -rf .tmp_versions
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/usr/src/kernel-headers-2.6.
   16-ck12 SYSOUT=/usr/src/kernel-headers-2.6.16-ck12'...
   
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /usr/src/kernel-headers-2.6.16-ck12 SUBDIRS=
   /home/poison/NVIDIA-Linux-x86-1.0-8762-pkg1/usr/src/nv modules
   /usr/src/kernel-headers-2.6.16-ck12/arch/i386/Makefile:38: /usr/src/kernel-h
   eaders-2.6.16-ck12/arch/i386/Makefile.cpu: No such file or directory
   make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.16-ck12/arc
   h/i386/Makefile.cpu'.  Stop.
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

Well i used install and i get pretty much the same thing

---

### Post by tseliot on 2006-06-24
> **PoisoN2003]```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Jun 24 15:57:20 2006

option status:
  license pre-accepted    : true
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: true
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : true
  silent                  : true
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/lib/xorg/
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/kernel-headers-2.6.16-ck12
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : none
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using built-in stream user interface
-> License accepted by command line option.
-> Not probing for precompiled kernel interfaces.
-> Performing CC test with CC="cc".
-> Using the kernel source path '/usr/src/kernel-headers-2.6.16-ck12' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Kernel output path: '/usr/src/kernel-headers-2.6.16-ck12'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv said:**
> : *** No rule to make target `/usr/src/kernel-headers-2.6.16-ck12/arc
   h/i386/Makefile.cpu'.  Stop.
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [mdl] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

Well i used install and i get pretty much the same thing
Did you install the kernel headers for your kernel (you compile them, didn't you?)?

---

### Post by PoisoN2003 on 2006-06-24
yeah i did but only afterwords but now i reinstalled the kernel and updated it hopefully it works ill try your script again and reply here

Well now it works just no sound

---

### Post by yetterben on 2006-07-02
i get this error upon intial install.

NVIDIA:no device section for instance bus id pci 2:11:0
no device detected

nvidia fx 5200
this is where my card is in windows. cant even run live cd to begin install tried updateing modules and nothing any input would tock

Thanx

---

### Post by tseliot on 2006-07-02
[QUOTE=yetterben]i get this error upon intial install.

NVIDIA:no device section for instance bus id pci 2:11:0
no device detected

nvidia fx 5200
this is where my card is in windows. cant even run live cd to begin install tried updateing modules and nothing any input would tock

Thanx[/QUOTE]
1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

---

### Post by ubuntu_demon on 2006-07-03
I linked to this great thread on my blog : [http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

---

### Post by ezphilosophy on 2006-07-03
I really want to get compiz/xgl working but as I said before, it seems to remove what was done by the envy script.  

At this point, I'm just not sure if my graphics card is working properly!  When I go to system tools> nvidia X server settings, it doesn't list my card.

When I run the envy script again, it says that the system has been altered and I should remove the path or change the target.  Possibly, everything is installed right except for the x settings tool.

---

### Post by tseliot on 2006-07-05
[QUOTE=ezphilosophy]I really want to get compiz/xgl working but as I said before, it seems to remove what was done by the envy script.  

At this point, I'm just not sure if my graphics card is working properly!  When I go to system tools> nvidia X server settings, it doesn't list my card.

When I run the envy script again, it says that the system has been altered and I should remove the path or change the target.  Possibly, everything is installed right except for the x settings tool.[/QUOTE]
Try opening Nvidia settings in this way:
```
nvidia-settings -c :0
```

---

### Post by ezphilosophy on 2006-07-06
[QUOTE=tseliot]Try opening Nvidia settings in this way:
```
nvidia-settings -c :0
```[/QUOTE]
  

I did that and I got:
```
ez@ezphilosophy:~$ nvidia-settings -c :0

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0'.

ez@ezphilosophy:~$

```

---

### Post by arjaybe on 2006-07-08
tseliot:

I just wanted you to know that your suggestions worked for me.  I did an upgrade from Ubuntu64 5.10 to 6.06 and had the xserver problem, so I booted single and did apt-get install xserver-xorg-driver-via (for my Unichrome graphics) and dpkg-reconfigure xserver-xorg.  After reboot I got into a beautiful new desktop.

Thanks a lot.

---

### Post by tseliot on 2006-07-09
> **ezphilosophy said:**
> I did that and I got:
```
ez@ezphilosophy:~$ nvidia-settings -c :0

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0'.

ez@ezphilosophy:~$

```
Try a number other than 0?

---

### Post by ezphilosophy on 2006-07-09
> **tseliot said:**
> Try a number other than 0?

```
ez@ezphilosophy:~$ nvidia-settings -c :1

ERROR: Cannot open display ':1'.

ez@ezphilosophy:~$ nvidia-settings -c :2

ERROR: Cannot open display ':2'.

ez@ezphilosophy:~$ nvidia-settings -c :0

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0'.

ez@ezphilosophy:~$

```

Thanks for any ideas.

---

### Post by Choad on 2006-07-12
i have a toshiba satellite 3000 x4

its got an intel i810 graphics card that runs sweet with xfree86. i have tried so many ways of getting it to work in xorg... no avail

can i get dapper to play nice with xfree?

---

### Post by tseliot on 2006-07-12
> **Choad said:**
> i have a toshiba satellite 3000 x4

its got an intel i810 graphics card that runs sweet with xfree86. i have tried so many ways of getting it to work in xorg... no avail

can i get dapper to play nice with xfree?
I guess not.

Anyhow your card is supported by xorg.

What do you mean when you say that it doesn't work? The xserver crashes or what?

And did you do a fresh install of Dapper?

---

### Post by Choad on 2006-07-12
> **tseliot said:**
> I guess not.

Anyhow your card is supported by xorg.

What do you mean when you say that it doesn't work? The xserver crashes or what?

And did you do a fresh install of Dapper?
fresh install, it gives me some error at the beggining.... can't remember what it says ill find out some time. but anyway thats like... right at the beggining just after grub but before the "ubuntu" logo appears. it ignores that and then procedes. if i have a server install (and therefor the text-mode loading screen) it also says something about hw_random not being able to be loaded

after it loads it starts x, and i think that "it" thinks it has all worked. because if it thought something was wrong it would just shut down X it's self... am i correct? well anyway, the screen is blank but with a few kind of sweeping grey patterns going on... and then it just settles down to one shade of dark grey.

i can set the graphics driver to vga, and it works but cga is laaaaaaame! vesa does the exact same thing as i810

i have made a thread about my problem [http://www.ubuntuforums.org/showthread.php?t=213549](http://www.ubuntuforums.org/showthread.php?t=213549) there

i have now tried installing with the alternate cd since writing that original post

as i said, it worked flawlessly in xfree86 with the i810 driver.

i hope someone can help!

---

### Post by tseliot on 2006-07-13
> **Choad said:**
> fresh install, it gives me some error at the beggining.... can't remember what it says ill find out some time. but anyway thats like... right at the beggining just after grub but before the "ubuntu" logo appears. it ignores that and then procedes. if i have a server install (and therefor the text-mode loading screen) it also says something about hw_random not being able to be loaded

after it loads it starts x, and i think that "it" thinks it has all worked. because if it thought something was wrong it would just shut down X it's self... am i correct? well anyway, the screen is blank but with a few kind of sweeping grey patterns going on... and then it just settles down to one shade of dark grey.

i can set the graphics driver to vga, and it works but cga is laaaaaaame! vesa does the exact same thing as i810

i have made a thread about my problem [http://www.ubuntuforums.org/showthread.php?t=213549](http://www.ubuntuforums.org/showthread.php?t=213549) there

i have now tried installing with the alternate cd since writing that original post

as i said, it worked flawlessly in xfree86 with the i810 driver.

i hope someone can help!
I have replied there

---

### Post by Choad on 2006-07-14
> **tseliot said:**
> I have replied there
im still having problems mate!

---

### Post by ch424 on 2006-07-14
I used the solution you said in [post #71](http://www.ubuntuforums.org/showpost.php?p=1130109&postcount=71), and it worked great, thanks!

Using X800XT (AGP)
Athlon64 with 64bit alernate version of 6.06
Viewsonic VX912 monitor on DVI

Thanks again

ch424

---

### Post by tseliot on 2006-07-15
> **Choad said:**
> im still having problems mate!

I've replied there again.

---

### Post by jolene on 2006-07-16
> **pjs_flyer said:**
> Hi

I followed the instructions, and everything seems to work until I get to dpkg-reconfigure gdm, which throws up the error:

invoke-rc.d: initscript gdm, action "reload" failed

If I press on regardless, I get the ubuntu logo, the scrolling messages, then a brief blank screen, the brown background with the little spinny wheel thing, then it freezes.  Any ideas?

I'm using an amilo a1630 laptop (amd64) with an ATI Mobility Radeon 9700 card. Any help greatle appreciated...
I have the same problem with the dpkg-reconfigure gdm command, but I do not get as far as the Ubuntu logo if I continue, it more kind of flashes between the "failed to start the X server" message and back a few times before it stops on the "failed to start" message (to my dismay). 

If I use your apt-get -f install suggestion instead, tseliot, I get a lot of "couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-updates/multiverse Packages... stat (2 No such file or directory)" messages (for multiverse, universe, main and restricted packages) and a suggestion that I run apt-get update.

I have a horrible suspicion this might be my fault because my friend had set some updates to download after he installed Ubuntu for me on Thursday, and when it got to the end of the download and told me it had not been able to download some apts, I was too tired to call my friend and ask him what to do next, so I shut down the computer and went to sleep.

I am bewildered, please help, in short words, please.

---

### Post by tseliot on 2006-07-16
> **jolene said:**
> If I use your apt-get -f install suggestion instead, tseliot, I get a lot of "couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-updates/multiverse Packages... stat (2 No such file or directory)" messages (for multiverse, universe, main and restricted packages) and a suggestion that I run apt-get update.

Try with:
```
sudo apt-get update
```

and tell me what happens (and what it says)

---

### Post by Choad on 2006-07-16
> **jolene said:**
> I have the same problem with the dpkg-reconfigure gdm command, but I do not get as far as the Ubuntu logo if I continue, it more kind of flashes between the "failed to start the X server" message and back a few times before it stops on the "failed to start" message (to my dismay). 
[B]
If I use your apt-get -f install suggestion instead, tseliot, I get a lot of "couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) dapper-updates/multiverse Packages... stat (2 No such file or directory)" messages (for multiverse, universe, main and restricted packages) and a suggestion that I run apt-get update.
[/B]
I have a horrible suspicion this might be my fault because my friend had set some updates to download after he installed Ubuntu for me on Thursday, and when it got to the end of the download and told me it had not been able to download some apts, I was too tired to call my friend and ask him what to do next, so I shut down the computer and went to sleep.

I am bewildered, please help, in short words, please.
helps to have an internet connection ;)

---

### Post by jolene on 2006-07-16
Says the same thing as before ("Couldn't stat source package list...") then "Some index files failed to download, they have been ignored, or old ones used instead". And it still fails to start.

OK, OK, Choad, an internet connection would be a bonus, but how do I connect to the internet if I cannot start the system, hey, mister?? ;)

---

### Post by Choad on 2006-07-16
> **jolene said:**
> Says the same thing as before ("Couldn't stat source package list...") then "Some index files failed to download, they have been ignored, or old ones used instead". And it still fails to start.

OK, OK, Choad, an internet connection would be a bonus, but how do I connect to the internet if I cannot start the system, hey, mister?? ;)
i assumed that by "i tried your apt-get -f install" you had access to the command line interface

if you can get to the cli, you can get an internet connection ;)

(trust me, it is worth learning the steps, it saves your *** when you accidentally bork X)

for example with a wifi connection using ndiswrapper (which is how i do it)

$sudo apt-get install ndiswrapper-utils 
(this is from the cd)
$sudo ndiswrapper -i /path/to/driver.inf
$sudo modprobe ndiswrapper
(card is now working)
$sudo ifconfig wlan0 up
$sudo iwconfig wlan0 essid YOUR_ESSID
$sudo dhclient wlan0
(connected to the network)


im still having [problems](http://www.ubuntuforums.org/showthread.php?t=213549)  with my X server tho! (i dont know if you check the other thread tseliot

---

### Post by jolene on 2006-07-17
OK, my friend taught me to "ping", seems I do have an internet connection... But we have concluded that I should reinstall with a newer version of Ubuntu. Thank you for your help, Master Roaster and Carafe. This is all a bit godlike. :cool:

---

### Post by LCC on 2006-07-17
I am having the same problem, if I update from 5.10 I can update but when I reboot the machine and try to start ubuntu a black screen is what comes up, so I tried to change in the xserver ati to vesa and vga as well, dint work, then I tried to change to the proprietary driver (fglrx) and dodnt work either, for some reason I cant burn the cd image right, I downloaded and burned ubuntu 6.06 several times from ubuntu 5.10 and windows xp as well and still when I check for error they always comes up then I cannot try a installation from zero.any ideas???


AMD 64 X2 4400 
Asus A8N-SLI Deluxe Nforce4
1024 mb ram
ATI Radeon Xpress 800 256mb
80 gb and 300 gb HDD
2 gb of swap/ 20gb home

---

### Post by tseliot on 2006-07-17
> **LCC said:**
> I am having the same problem, if I update from 5.10 I can update but when I reboot the machine and try to start ubuntu a black screen is what comes up, so I tried to change in the xserver ati to vesa and vga as well, dint work,
Did you follow exactly the steps I suggest in this thread?

> **LCC said:**
> then I tried to change to the proprietary driver (fglrx) and dodnt work either, for some reason I cant burn the cd image right, I downloaded and burned ubuntu 6.06 several times from ubuntu 5.10 and windows xp as well and still when I check for error they always comes up then I cannot try a installation from zero.any ideas???

Try burning the CD at a lower speed ( e.g. 4X )

---

### Post by LCC on 2006-07-18
U tryed it again and I done, updated from 5.10 to 6.06 with the updated manager, then the only resolution that allowed me to login in the graphic mode was vga and it was really weird, 300x280(I think) couldn`t do much then I did something wrong and it would let me login again so I am starting everithing from zero,if I install the proprietarary driver found at ATI`s website it should work shouldn`t it, but I am strugling to install it and if I install it on 5.10 it should stay as option when I upgrade to 6.06 shouldn`t, how do I install this driver, cause I download it then when I try to install it says 

gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.

and when I try to install by terminal it says that it couldn`t find the package. thans for the help

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

I am now trying to follow this page from wiki, but I I am pretty new to linux, and even following steps sometimes is hard, lol, 

sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)[COLOR="Red"]to get whatever I have to change for uname I type uname in the terminal and it shows me the version of the kernel right?[/COLOR] #Okay if it is already installed
sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver and 64-bit users should deselect int10a

64-bit users:

You have to downgrade to an older version of libdri.a due to an incompatilbity with the ATI drivers. Download it here

Change to download directory:

gunzip libdri.a.gz    [COLOR="Red"]in this part when I type in the terminal it says no such file or directory, I stoped here [/COLOR]
sudo cp /usr/X11R6/lib/modules/extensions/libdri.a libdri.a.old
sudo cp libdri.a /usr/X11R6/lib/modules/extensions/

---

### Post by ezphilosophy on 2006-07-18
Does the envy script work with Kubuntu Dapper?

---

### Post by tseliot on 2006-07-19
> **ezphilosophy said:**
> Does the envy script work with Kubuntu Dapper?

Yes, sure

---

### Post by tseliot on 2006-07-19
> **LCC said:**
> if I install the proprietarary driver found at ATI`s website it should work shouldn`t it, but I am strugling to install it and if I install it on 5.10 it should stay as option when I upgrade to 6.06 shouldn`t, how do I install this driver, cause I download it then when I try to install it says
Do you want to Install 5.10, then install the driver and upgrade to 6.06, right?

Please don't do it. That's one of the best ways to make a mess on you OS. The kernel would be updated but the ATI module would not.

A fresh install of Dapper + installing the ATI driver is the best thing to do.


IF you don't want to reinstall Ubuntu and still have the problem with the resolution you can try this:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)

---

### Post by rmjb on 2006-07-19
> **tseliot said:**
> 1) Did you try "vga" driver instead of "vesa"?

2) If you already did you can try installing ATI's proprietary driver:
```
sudo apt-get install xorg-driver-fglrx linux-restricted-modules-`uname -r`
```

Make sure you use a ` instead of a '

then:
```
sudo dpkg-reconfigure xserver-xorg
```

and select "fglrx" driver

Well, this worked for me. After having xserver crash on me when booting the live cd and the same effect when choosing vga, then having the entire PC crash (blank screen, non responsive keyboard) when choosing vesa or "Safe Graphics Mode" using the fglrx drivers worked, and on Kubuntu 64 also.

Thanks,
- rmjb

---

### Post by SuperMike on 2006-07-20
I had a case of booting with two different video cards for Xinerama mode in Breezy before upgrading to Dapper. One was ati and the other was nvidia. On reboot, it booted up to the point of loading the gdm login manager and then hard-locked. I had no choice but reboot. Not even CTRL+ALT+F1 would help me out in getting any kind of response.

Turns out that Xinerama doesn't work anymore in Dapper. It's listed this way on Launchpad. I hear it might not work until Edgy comes out. However, there was a great fix for me that allowed me to forget about Xinerama forever.

Luckily for me, I could remove one of the video cards (the nvidia one) and leave the dual-head ATI card in there. Previously I could never get it to work, but in Dapper's Xorg 7, it works. My ATI card has a funky adapter port and a special cable with two SVGA cable connections coming out to attach two separate monitors.

I had to boot up to rescue mode and then do:

dpkg-reconfigure xserver-xorg

and go with the defaults.

Once done, I edited the /etc/X11/xorg.conf file, found the ATI device section, and added this extremely obscure option that hardly anyone knows about. Found this info at a blog on the Novell site, oddly enough.

Option "CRT2Position" "RightOf"

I also removed this:

Option "Xinerama" "on"

Once I rebooted, I then went to Screen Resolution control panel and chose an extra wide screen resolution. If you don't have that option, then you have to play with your xorg.conf monitor Horiz and Vert refresh hertz in the monitor section, plus resolution values in the Screen section, until you get the ability to set an extra wide desktop. In my case, I set it to an extra wide desktop and now all of a sudden I have something that runs exactly like Xinerama mode, 100 percent.

So Xinerama, no more. I now have an obscure ATI option called CRT2Position that achieves the exact same thing.

Note, however, that I couldn't get 3ddesk to install. When I run it, it spits out:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.

Oh, well, no hardware acceleration is possible. Guess I'll just forget about needing that.

---

### Post by madas91 on 2006-07-22
Hi am new to all this and having problems installing with xserver and the dektop cd.
All goes fine untill the screen blacks out with cursor at topm  left. i think its querying video card then i get the message"failed to start x-server. It is likely it is not set up correctly would you like to view the xserver output to diagnose the problem"
There is a yes or no box available.


System is MSI K8n neo4
          AMD64 4000+
          Asus eax800xl 256
          40G seagate drive on IDE master
          1.5Gb ram at 400mhz

Any help getting round this problem would be much appreciated

---

### Post by tseliot on 2006-07-22
> **madas91 said:**
> Hi am new to all this and having problems installing with xserver and the dektop cd.
All goes fine untill the screen blacks out with cursor at topm  left. i think its querying video card then i get the message"failed to start x-server. It is likely it is not set up correctly would you like to view the xserver output to diagnose the problem"
There is a yes or no box available.


System is MSI K8n neo4
          AMD64 4000+
          Asus eax800xl 256
          40G seagate drive on IDE master
          1.5Gb ram at 400mhz

Any help getting round this problem would be much appreciated
Try booting the CD in Safe mode

---

### Post by madas91 on 2006-07-23
ok i redownloaded the 32bit version on cd and had same problem but all worked fine in safe mode :)

Just installed graphic drivers from repository and had the same problems as at the start of this post but thanks to previous advice  i'm up and running and learning fast

Thanks again for this help to us novices and not so novices alike

---

### Post by tseliot on 2006-07-23
> **madas91 said:**
> ok i redownloaded the 32bit version on cd and had same problem but all worked fine in safe mode :)

Just installed graphic drivers from repository and had the same problems as at the start of this post but thanks to previous advice  i'm up and running and learning fast

Thanks again for this help to us novices and not so novices alike
1) Try this:
```
sudo dpkg-reconfigure xserver-xorg
```

and set the driver to "vesa". Press ENTER if you don't know the answer to the other questions.

2) If you want to install the proprietary driver you can try this guide:
[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

### Post by arkaos on 2006-07-26
> **tseliot said:**
> If the Xserver crashes at boot, then this quick fix might do the trick for you.

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Make sure that everything went fine during the update:
```
dpkg --configure -a
```

3) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

4) Reconfigure the login manager:
```
dpkg-reconfigure gdm (if you use Ubuntu or Xubuntu)
```
or
```
dpkg-reconfigure kdm (if you use Kubuntu)
```

and select your desired login manager (either gdm or kdm, according to the version of Ubuntu you're using or to your personal preference)

5) Restart your computer:
```
reboot
```



Dude...you are a GENIUS! I xserver crashed after I installed the nvidia-glx drivers according to the instructions from another thread. nvidia said it installed correctly, but the xserver crashed on next reboot. per your instructions, I was able to reconfigure AND select the correct installed driver for my vid card AND I FINALLY got the OpenGL 3d accel I have been trying to get working for DAYS. Thanks a billion! :)

---

### Post by arkaos on 2006-07-26
OOOOOH YEAH! Blender is working NOW.....YES! Thanks again :)

---

### Post by Zanathel on 2006-08-12
I do have two 3d-cards: one internal and GeForce 2.
I'd like Ubuntu to detect GeForce 2, because the internal does not work... but that seems impossible. The fact that Ubuntu insists selecting the internal video card has led to a black non-responsive screen after boot.

What shall I do?

---

### Post by tseliot on 2006-08-12
> **Zanathel said:**
> I do have two 3d-cards: one internal and GeForce 2.
I'd like Ubuntu to detect GeForce 2, because the internal does not work... but that seems impossible. The fact that Ubuntu insists selecting the internal video card has led to a black non-responsive screen after boot.

What shall I do?

post the result of this command:
```
lspci
```

---

### Post by zanoni on 2006-09-24
Hello Alberto,

I have installed the fglx Ati driver (8.25.18) for my radeon 9800pro. It's working this 3D rendering.

But I have these warnings in Xorg.0.log
Quote:
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8

How it's posible to find solution about this ?

Thank in avance.

---

### Post by tseliot on 2006-09-25
> **zanoni said:**
> Hello Alberto,

I have installed the fglx Ati driver (8.25.18) for my radeon 9800pro. It's working this 3D rendering.

But I have these warnings in Xorg.0.log
Quote:
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Specified desktop setup not supported: 8

How it's posible to find solution about this ?

Thank in avance.

If that doesn't cause you any problem then you shouldn't worry about.

---

### Post by gerowen on 2006-10-25
I'm using a 256MB NVidia GeForce FX 5500.  I'm currently running Fedora Core 5, but wanted to try Ubuntu because I heard it was a really good desktop Linux, and given the fact that it's 1 CD instead of 5, I'm assuming it's a lot less bloated than Fedora Core.  Anyway, following the initial instructions I get a message telling me that xserver-xorg-driver-via is already installed and up to date.  So then I try installing some nvidia driver packages(couldn't quite remember all of them).  I do sudo apt-get install nvidia-glx .  However the old driver package I use in FC5 (kmod-nvidia) doesn't work, it just says it doesn't exist.  Anyway, after installing nvidia-glx, NVIDIA now shows up as a driver set when I do dpkg-reconfigure xserver-xorg.  However after that nothing changes, I still get "no devices detected" only this time it says NVIDIA instead of VESA, and I get shot straight back to a command line.  Help anyone?

A suggestion for later releases, include ati and nvidia drivers for the kernel version on the CD.  Would make it a lot more user friendly to Linux n00bs.

Edit:  You could also just include a generic driver for situations like this.  FC5 just booted a default driver, and sure it looked crappy, but using gui package managers to find the correct package is easier than trying to read command line text if you're not sure what you're looking for.

---

### Post by muxecoid on 2006-10-28
All OpenGL apps stopped working after upgrading to Edgy. [http://www.ubuntuforums.org/showthread.php?t=286881](http://www.ubuntuforums.org/showthread.php?t=286881) What needs to be done?


Attempted to reconfigure xserver as advices in this thread in it stopped working at all :(

---

### Post by tseliot on 2006-10-29
> **marcusdean.adams said:**
> However the old driver package I use in FC5 (kmod-nvidia) doesn't work, it just says it doesn't exist.
That's because Ubuntu is not Fedora

[QUOTE=marcusdean.adams;1662550]Anyway, after installing nvidia-glx, NVIDIA now shows up as a driver set when I do dpkg-reconfigure xserver-xorg.  However after that nothing changes, I still get "no devices detected" only this time it says NVIDIA instead of VESA, and I get shot straight back to a command line.  Help anyone?
Follow method 1 of this guide of mine (you can do it from the command line):
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

> **marcusdean.adams said:**
> A suggestion for later releases, include ati and nvidia drivers for the kernel version on the CD.  Would make it a lot more user friendly to Linux n00bs.
It can't be done since the NVidia and the ATI driver are proprietary and therefore won't be included in Ubuntu by default.

> **marcusdean.adams said:**
> Edit:  You could also just include a generic driver for situations like this.  FC5 just booted a default driver, and sure it looked crappy, but using gui package managers to find the correct package is easier than trying to read command line text if you're not sure what you're looking for.
That's something which should be implemented.

---

### Post by gerowen on 2006-10-29
Yeah I managed to get it all working, my problem the whole time was that I was specifying the wrong PCI address for my card, I'd forgotten all about this topic, :p.

---

### Post by Scheater5 on 2006-10-29
Just wanted to let ya know that your advice saved my comp.  This thread is about Dapper, but an upgrade to Edgy killed the X server  on my comp.  I was about to go insane when I found this thread browsing on Lynx (which, BTW, is a great resource when you have no other recourse).  
More details [here]("http://ubuntuforums.org/showthread.php?t=288037").

---

### Post by grkravi on 2006-10-31
> **tseliot said:**
> If the Xserver crashes at boot, then this quick fix might do the trick for you.

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Make sure that everything went fine during the update:
```
dpkg --configure -a
```

3) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

4) Reconfigure the login manager:
```
dpkg-reconfigure gdm (if you use Ubuntu or Xubuntu)
```
or
```
dpkg-reconfigure kdm (if you use Kubuntu)
```

and select your desired login manager (either gdm or kdm, according to the version of Ubuntu you're using or to your personal preference)

5) Restart your computer:
```
reboot
```

Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga".

**[COLOR="Red"]NOTE: if you're using a VIA graphic card try this:[/COLOR]**
```
apt-get install xserver-xorg-driver-via
```
then
```
dpkg-reconfigure xserver-xorg
```
and select your Via card (and driver)

P.S. After you're able to use the Desktop Environment I suggest you to install the right drivers for your graphic card in order to make the most of it.


**IF you have an ASUS P5VDC-MX motherboard + onboard VIA**
sudo nano -w /boot/grub/menu.lst

Look for a line which begins with "kopt":
```
# kopt=root=/dev/hdc1 ro
```

and add "pci=conf1" on that line:
```
# kopt=root=/dev/hdc1 ro pci=conf1
```

CTRL+X to exit (save the file)

Then type:
```
sudo update-grub
```

and reboot.

Now the xserver should work fine.

I followed these steps, used vesa and vga aswell, both failed
during the dpkg-reconfigure gdm.
Error is : invoke-rc.d: initscript gdm, action "reload" failed.
Hitting black screen again at reboot.

---

### Post by tuxedobuford on 2006-11-02
Would this method/technique still apply if the Xserver issue relates to font files? I upgraded to Edgy from Dapper and encountered some errors I thought were minor. Like a dolt, I chose to ignore them and proceed. I now get an error that refer an invalid font location for the 100dpi, 75dpi, etc fonts. When I boot, everything seems to be going fine. The new Ubuntu splash is displayed after watching the typical text portion of the boot and just when it should pop up the login screen, i get the XServer error instead. It says to run mkfontdir but this doesn't seem to make any difference. Will reconfiguring the Xserver fix a potentially invalid font file location reference.? Incidentally, the fonts are still in the respective directories. Until my upgrade foible, i was running a rock solid Toshiba Satellite with Dapper installed.

Thanks.

---

### Post by frozen chosen on 2006-11-03
I have problems when starting edgy this includes dapper but not warty.
my load scream comes up ok but then it gos dark and my montor clicks some times up to three time then gos dark or comes up and works great, but I have had to reboot up to 5 times to get it up.
 I have a all in wonder ati 8500 agp with a amd athlon xp 1800,checking my
xserver conf saids my drivers are ati. I have tryed  loading other drivers
useing the x terminal and some commands in your thread and it get to card location and freezes .
 Hope someone  can help me and I am in the right place
                                 
                                                    Thank you
                                                    Frozen chosen

---

### Post by grkravi on 2006-11-03
I was able to make progress in this black screen issue by changing my driver from vesa to trident. My Dell Inspiron 5160 has XGI VOLARI XP5 video card and vesa was working fine with Dapper. But in Edgy, i shifted to Trident driver and included the modeline from /var/log/Xorg.0.log in the /etc/X11/xorg.conf file.
Both gnome and KDE desktops are up but i still have a minor issue, when i move a window like terminal or browser, it gets blurred and i have to start/refresh the window again.

---

### Post by Sterkenburg on 2006-11-07
Edit:  I hadn't tried using my graphics card manufacturer's drivers.  lol.

---

### Post by Mujaheiden on 2006-12-22
I tried to upgrade from breezy to LTS 6.06 - badger, but now my xserver doenst work, also with none of the tips i got from fora.
It is also something about my mouse and keyboard not being detected, but i give you the lspci output. Some tips?
```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)
``` and heres part of my xorg.0.log ```
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(II) LoadModule: "mouse"
(WW) Warning, couldn't open module mouse
(II) UnloadModule: "mouse"
(EE) Failed to load module "mouse" (module does not exist, 0)
(...)
(EE) No Input driver matching `kbd'
(EE) No Input driver matching `mouse'
(WW) No core pointer registered
No core keyboard

Fatal server error:
failed to initialize core devices
```

tips are welcome.

edit: I got stupid sources.lists for upgrading breezy into dapper, and this broke almost everything. after finding a proper sources.list, and doing all the upgrade and dist-upgrades, everything worked as it should.

---

### Post by jake3988 on 2007-01-18
What happens if I can't logon to the recovery mode?  X won't boot the normal way, claiming it gives an 'internal error' but recovery hangs when trying to load some module (Unless it just takes a while?)

anyway, I'm fairly certain all I need to do is reconfigure gdm and I'll be set, but I can't get recovery to load all the way.


(I got to this point by doing the 'fresh kernel' method of getting alsa drivers and it deleted gdm and gnome so I reinstalled them and now all it says it won't load to due an internal error)

---

### Post by nemanaldin on 2007-01-31
hi
i cant login to ubuntu 6.06 and show these errors plz help me

[http://i18.tinypic.com/2py9kjp.jpg](http://i18.tinypic.com/2py9kjp.jpg)
[http://i16.tinypic.com/2hd0dok.jpg](http://i16.tinypic.com/2hd0dok.jpg)
[http://i12.tinypic.com/2ij5579.jpg](http://i12.tinypic.com/2ij5579.jpg)

and i write thsi command and:
more .xsession-errors
[http://i7.tinypic.com/47v6t13.jpg](http://i7.tinypic.com/47v6t13.jpg)

and this:> sudo aptitude update
sudo aptitude install ubuntu-desktop

i tested that commands but my problem still not solve
ask of this command sudo aptitude
[http://i5.tinypic.com/2h2jgif.jpg](http://i5.tinypic.com/2h2jgif.jpg)
and this sudo aptitude install ubuntu-desktop
[http://i7.tinypic.com/29da7t5.jpg](http://i7.tinypic.com/29da7t5.jpg)
thanks very much

---

### Post by nemanaldin on 2007-01-31
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


Section "Files"
	
FontPath	"/usr/share/X11/fonts/misc"
	
FontPath	"/usr/share/X11/fonts/cyrillic"
	
FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	
FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	
FontPath	"/usr/share/X11/fonts/Type1"
	
FontPath	"/usr/share/X11/fonts/100dpi"
	
FontPath	"/usr/share/X11/fonts/75dpi"
	
# path to defoma fonts
	
FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection



Section      "Module"
	
Load	"bitmap"
	
Load	"ddc"
	
Load	"dri"
	
Load	"extmod"
	
Load	"freetype"
	
Load	"glx"
	
Load	"int10"
	
Load	"type1"
	
Load	"vbe"

EndSection



Section                      "InputDevice"
	
Identifier	                  "Generic Keyboard"
	
Driver		"kbd"
	
Option		"CoreKeyboard"
	
Option		"XkbRules"	"xorg"
	
Option		"XkbModel"	"pc104"
	
Option		"XkbLayout"	"us"

EndSection



Section "InputDevice"
	
Identifier	"Configured Mouse"
	
Driver		"mouse"
	
Option		"CorePointer"
	
Option		"Device"		"/dev/input/mice"
	
Option		"Protocol"		"ExplorerPS/2"
	
Option		"ZAxisMapping"		"4 5"
	
Option		"Emulate3Buttons"	"true"

EndSection



Section "InputDevice"
  
Driver        "wacom"
  
Identifier    "stylus"
  
Option        "Device"        "/dev/wacom"         # Change to 
                                                      
# /dev/input/event
                                                      
# for USB
  
Option        "Type"          "stylus"
  
Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY

EndSection



Section "InputDevice"
  
Driver        "wacom"
  
Identifier    "eraser"
  
Option        "Device"        "/dev/wacom"          # Change to 
                                                      
# /dev/input/event
                                                      
# for USB
  
Option        "Type"          "eraser"
  
Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY

EndSection



Section "InputDevice"
  
Driver        "wacom"
  
Identifier    "cursor"
  
Option        "Device"        "/dev/wacom"          # Change to 
                                                      
# /dev/input/event
                                                      
# for USB
  
Option        "Type"          "cursor"
 
 Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY

EndSection



Section "Device"
	
Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	
Driver		"nv"
	
BusID		"PCI:1:0:0"

EndSection



Section "Monitor"
	
Identifier	"F700P"
	
Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection

Section "Screen"
	
Identifier	"Default Screen"
	
Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	
Monitor		"F700P"
	
DefaultDepth	24
	
SubSection "Display"
		
Depth		1
		
Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

SubSection "Display"
		
Depth		4
		
Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

SubSection "Display"
		
Depth		8
		
Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	
SubSection "Display"
		
Depth		15
		
Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

SubSection "Display"
		
Depth		16
		
Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	
SubSection "Display"
		
Depth		24
		
Modes                "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection

EndSection


Section "ServerLayout"
	
Identifier "Default Layout"
	
Screen"Default Screen"
	
InputDevice"Generic Keyboard"
	
InputDevice"Configured Mouse"
	
InputDevice "stylus" "SendCoreEvents"
	
InputDevice "cursor" "SendCoreEvents"
	
InputDevice "eraser" "SendCoreEvents"

EndSection


Section "DRI"
	
Mode	0666

EndSection

```

---

### Post by HellionDarkLord on 2007-02-17
I finally got everything working to the point where I can actually use the desktop after upgrading to edgy.  It turns out that the xserver is at fault.  My only problems now is that I cannot scroll up because the screen goes retro on about three lines in the browser and displays only those three lines repeatedly across the browser window.

Everything else seems to work fine  (so far)

I know that I'm always going to have issues so long as I have a volari v3 XGI vid card.  The card isn't really that bad for only a mere $40.00 because it will play doom three when overclocked 30%.

So, what can I do about the scrolling problem?  I can scroll down no problem.  Tell me what you guys need to know and I will supply the info.

I'm using dkpg-reconfigure xserver-xorg  It thinks that I don't even have any video hardware installed, so I use the trident driver, and generic option.  framebuffering is used, and I know I have all the resolution settings right.

Is there a way to install the .rpm drivers from the XGI site?  or will they only work for redhat and suse?  I don't like either of those operating systems, but then again I had NO problems using this video card with dapper (6.06) and only have a problem after upgrading to Edgy (6.01)


thanks for any input.

---

### Post by eilker1917 on 2007-03-07
[http://ubuntuforums.org/showthread.php?t=377809](http://ubuntuforums.org/showthread.php?t=377809)

 i couldnt find any solution, i cant get login screen, 

it just happened after upgrading from 6.06 to 6.10.

---

### Post by Tom B on 2007-03-08
I was reconfiguring the xserver and everything seemed to be working fine, but when it asked about color depth and I hit "Enter" a message at the bottom of the screen came up that said "server-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/x11/xorg.conf.2007...." Then it returns me to the default root@Ubuntu in the terminal, and I can't get the cursor back in the screen to continue doing the configuration. It seems like there's an obvious solution to this, but I can't figure it out.

EDIT: I was right, it was obvious. The configuration was done. I continued down the list of commands and it worked. Thanks for the HowTo!

---

### Post by SuperCow56 on 2007-04-23
how would I get to the GRUB menu?

---

### Post by antoine8168 on 2007-06-01
vesa and vga don't work with my s3 virge dx video card. What should I do?
Thanks.

---

### Post by tseliot on 2007-06-02
> **antoine8168 said:**
> vesa and vga don't work with my s3 virge dx video card. What should I do?
Thanks.
Try using "fbdev" instead of "vga"

---

### Post by antoine8168 on 2007-06-02
fbdev doesn't work...
Here is the screen i got after making "startx" :
[IMG]http://img358.imageshack.us/img358/1972/dsc00022ci0.jpg[/IMG]

---

### Post by antoine8168 on 2007-06-03
I've changed the video card for a matrox pci card and the problem remains the same. I will do your method again, tseliot, and maybe it would work but I've read on [http://www.x.org](http://www.x.org) that the matrox cards are also hard to install (need maybe the proprietary driver).
Thank you.

---

### Post by bert79 on 2007-06-23
I try to install ubuntu from a live cd and when i get the menu i chose "Start or Install ubuntu". The splash screen is ok and then i get a error saying that X-Server has Failed.i have tried all version of ubuntu and nothing.  i even trierd safe graphice mode nada.when i get some more cds ile try the alternate install version.  in the mean time can anyone help me.  btw, im new to linux.

---

### Post by piotrgal on 2007-07-09
Hi !

I'm trying to install Ubuntu 6.10 Desktop on new hardware (for some reasons I don't want to use the newest 7.x). When the CD boots and I choose to install it, then after some nice progress bars the Xserver completely crashes with some kind of initialization failure and not recognized graphics card (I have NV 8600 GT). The errors look very similar to the screenshot in one of the last posts. Of course I can understand that, because it just can't have drivers for all hardware. But the problem is that it crashes in the same way also when using safe graphics mode, so I have no opportunity to install Ubuntu now. My question is - does exist ANY METHOD to force the installer to use just standard VGA driver for installation ??? All advices in this thread are for Ubuntu already working in text mode, but how to do it during install ?? I have tried also changing VGA modes and few kernel boot options about installation troubleshooting found on Ubuntu docs site, but all of them didn't help me. I can try to use an alternate CD, but is there ANY WAY to force Live CD to boot in standard VGA ??? (by specifying a kernel boot option ?). What is more strange for me, the installer already can use graphics mode at first stages after booting, so why the Xserver can't simply use default VGA in case of not recognized graphics card (quite usual case by the way) ???

Piotr

---

### Post by gregb49 on 2007-07-09
> **bert79 said:**
> I try to install ubuntu from a live cd and when i get the menu i chose "Start or Install ubuntu". The splash screen is ok and then I get a error saying that X-Server has Failed.It might be worth trying another distro such as Mepis, or KNOPPIX to see if this is a computer or Linux problem. Greg

---

### Post by beanco on 2007-09-09
> **tseliot said:**
> try with:
```
sudo apt-get install --reinstall gdm
```

hi, when I run the above I get

[PHP]W: Not using locking for read onl lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem[/PHP]


which gave me this


[PHP]
sudo dpkg --configure -a
dpkg: unable to access dpkg status area: Read-only file system[/PHP]
Any suggestions???

thanks

robi

---

### Post by hammudi on 2007-11-19
i installed ubuntu gutsy with the live cx with no problems (i have to edit the kernel before booting ubuntu and add "all_generic_ide" at the command line since i have ubuntu installed on my 2nd hdd).  i ran the update then activated the restricted driver for nvidia. when asked to reboot i did so but then it hangs after the ubuntu logo and status bar, not even a command is available.  when i select recovery console i end up at busybox with (initramfs) and a cursor.  i can't use sudo since it says sudo not found.  how do i disable the restricted driver?  you can say i am a beginner with ubuntu.  i have a dual boot setup with windows xp.  my card is an nvidia geforce go 6600 (laptop)

---

### Post by KjSlag on 2007-12-21
Hi, I'm new to Ubuntu and I have been working to get my ATI problems fixed for the past day and found a strage work-around. I'm sorry if this has already been posted or a solution already found.

When I boot Ubuntu in recovery mode and type exit, Ubuntu loads fine. Nothing else has worked for me yet.

I would greatly appreciate it if someone could tell me how to boot Ubuntu w/o doing this additional step. I hope this helps other's with similar problems.

More about my setup and Ubuntu problems.

If I try to load Ubuntu the normal way (at the screen where you choose your operating system), the screen goes black after displaying the 2 lines of text at the bottom (about he kernel).
my problems are most like melojo's on this thread:
{bah, lost the link, i'll post it later. i describe the important stuff below. melojo also had a x850 and AMD64}
I originally tried installing with the live CD, but that gave a similar black screen error (checking the CD also gave a similar error). I then successfully installed with the alternate CD, which worked with the exception of the black screen error when I try to load Ubuntu (checking this CD worked fine). I tried many of the suggestions on this thread:
dpkg --configure -a
dpkg-reconfigure xserver-xorg

the following line gave me an error message, i'll post it later if you want
dpkg-reconfigre gdm

I also tried modifying the /etc/X11/xorg.conf file with vi, changing the driver to "vesa" or "vga" from "ati" and adding the following option line:
Option "DRI" "off"

my comp:
AMD64 3500+
x850 saphhire
1536MB of ram
DELL E377c monitor

Thank You

EDIT:

Actually, if I specify my moniter while in Ubuntu, I have to go throught the whole dpkg-reconfigure xserver-xorg process before I can do the exit thing. I'll add more detail once I get my belkin pre-N card working.

---

### Post by bgracian on 2007-12-25
Just want to say "Thank you" to tseliot, if I understand the thread correctly.

While upgrading from 6.06 to 6.10 the process crashed only a few minutes from being finished, and I could only boot in recovery mode. Being a newbie, I had no idea how to proceed. 

Your suggestion to:    dpkg --configure -a
worked like a charm. 6.10 is now up and running and I'm looking forward to stepping up to 7.xx.

I also want to say that your specific, step-by-step instructions were the perfect solution for someone who had never typed in a line command before. 

Thanks again. :)

---

### Post by mrprowse on 2008-02-28
After lots of repeated failures trying to get this process to work with some budget computers (with no motherboard manuals) in my computer lab, I just copied the xorg.conf file from the install disk (which works fine) to the hard drive. (I've edited it to make it clearer for beginners after several students in my classroom had trouble following the directions!)

1. Boot up with the Ubuntu CD, selecting the first option (I think it says "Start or Install Ubuntu").

2. From the top menu, click on Places, then on Computer. A window will appear, and if you click on Filesystem, you should see an icon that looks suspiciously like your hard drive (it might say "18GB volume" or something). Click this icon, and Ubuntu will "mount" your drive-- the icon name should change to something like "disk" (mine mounted as **/media/disk** which I used in the command below).

3. From the top menu, click on Applications, then on Accessories, then on Terminal. You will get a blank window with a blinking cursor (for you n00bs out there, this is the command line). Type this command:

sudo cp /etc/X11/xorg.conf **/media/disk**/etc/X11/xorg.conf

You will be asked for your password. If you've never used the terminal before, note that your password won't show up as you type it, not even as asterisks (****); it will look like it's ignoring your input, but it's not-- just type your password and hit enter. If the command runs correctly, it will copy the xorg.conf file from the CD to your hard drive. If you get an error message, make sure you typed the line above **exactly** as shown.

4. Shutdown your computer, remove the boot disk, and then restart from your hard drive. This worked perfectly for me.

Hope this helps somebody!

:-j

---

### Post by gregb49 on 2008-02-28
> **mrprowse said:**
>  I just copied the xorg.conf fileThat's what I normally end up doing, but have gone about it in quite a torturous way, examining the xorg file, reconfiguring with **dpkg-reconfigure xserver-xorg** etc. Your method is simplicity itself, thanks. Greg

---

