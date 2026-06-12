---
title: "log-in screen"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by vitog on 2008-05-16
I have ubuntu 8.04 installed.  My log-in screen is so large that the log-in name is barely on the lower left of the screen.  How do I change the resolution of the opening screens.  The rest of the screen is working okay at 1024x768.  the log on screen must be 40x30 or some other rediculous resolution.

---

### Post by iaculallad on 2008-05-16
Edit your xorg.conf
sudo gedit /etc/X11/xorg.conf

Copy and paste the lines below which does not contain any asterisk to your "Screen" section.


*Section "Screen"
	*Identifier	"Default Screen"
	*Monitor		"Configured Monitor"
	*Device		"Configured Video Device"
	DefaultDepth 24
		SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
*EndSection

---

### Post by aysiu on 2008-05-16
If that doesn't work, you can try editing the boot menu:
[http://www.psychocats.net/ubuntu/startupmanager](http://www.psychocats.net/ubuntu/startupmanager)

I believe there's a display setting in one of those drop-down menus.

---

### Post by cvcuse on 2008-05-17
The ubuntu icon and a small part of the 'u' are showing on login screen,thus not able to login. Tried the 'start-up manger' using alternate cd 'fiesty' as upgrade to 'hh' via internet.No luck. I did try 'sudo dpkg-reconfigure xserver-xorg' only getting to 'mouse' choice and then message about not changing 'xorg'. Any advice  appreciated.

---

### Post by vitog on 2008-05-17
I looked at my /etc/x11/xorg.conf file and this is what was listed
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV10 [GeForce 256 SDR]"
	Monitor		"SylvaniaTF72"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"800x600@60"	"832x624@75"	"800x600@85"	"1024x768@85"	"800x600@75"	"1024x768@75"	"800x600@72"	"1024x768@70"	"800x600@56"	"1024x768@60"	"640x480@85"	"1024x768@43"	"640x480@75"	"1152x864@75"	"640x480@72"	"1280x960@60"	"640x480@60"	"1280x1024@60"	"1400x1050@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

I am reluctant to change anything beecause I am is the process of learning Linux
Thank you very much for any help.  Victor

---

### Post by cvcuse on 2008-05-17
Appreciate your reply.I went ahead and downloaded 'alt cd' of 'HH'. Had to do a little work with GParted cd to delete old "FF' which I had upgraded to "HH" via 'updates'..........everything working great. 
I too didn't like making any changes when not really understanding what was going on. If I can help,let me know.Thanks

---

### Post by vitog on 2008-05-21
I took the easy way out of my log on screen dilema by setting automatic log-on.  I didn't learn anything about fixing the system but I got past the problem.. It ia the chicken way out but it works.  :lolflag:

---

### Post by iaculallad on 2008-05-21
An easy way out but you did compromise a little bit of your system's security. Anyway, if that works for you without your user being asked for valid credentials (i.e: username and pass), so be it.

---

### Post by darkoblivion on 2008-06-22
hey guys, 

I just had the same exact problem. I went ahead and took the advice of both iaculallad and aysiu... so I'm not sure exactly which one worked. I thought I'd just give confirmation in this thread that my problem was resolved. 

However, after the login page was fixed, my regular resolution was altered, and then I had to play around with nvidia-settings and saving over xorg.conf to get that back to normal. 

So hats off to you guys, thanks!

---

### Post by kleo skywalker on 2008-06-22
I did both things - edited that file as *iaculallad* suggested, and edited the boot menu like *aysiu* said, but it made no difference to the resolution of my login screen. (It's always been higher than it should be.) Any other ideas?
Thanks.

---

### Post by kleo skywalker on 2008-06-23
bump

---

### Post by kleo skywalker on 2008-06-24
bumpety bump

---

### Post by kleo skywalker on 2008-06-25
Oh come on people, there can't not be a way to fix the log-in screen resolution in Ubuntu!

---

### Post by kleo skywalker on 2008-06-30
bump bump

---

### Post by kleo skywalker on 2008-07-06
bump!

---

### Post by kleo skywalker on 2008-07-14
I've never seen a thread with this many bumps on the forums before. Can no one tell me how to fix the resolution of the log-in screen in Hardy?

---

