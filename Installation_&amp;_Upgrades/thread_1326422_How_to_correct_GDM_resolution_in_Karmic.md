---
title: "How to correct GDM resolution in Karmic"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by anishd on 2009-11-14
*This is actually not a new problem to me..ubuntu traditionally did not detect gdm resolution correctly for me (I have installed ubuntu in many computers for last 4 years, most does not show gdm correctly). However, I could atleast see what is written on the screen even though resolution is not right.*

[B]Now, I have purchased a new LCD screen (1440x900 resolution).
GDM uses some other higher resolution so that the monitor display an error that "screen resolution is not correct. The correct resolution is 1440x900 60Hz" Because this error display mask, I cannot see the login screen, the username and password. I will have to wait till the monitor decide itself to stop the error message. [/B]

*I am really fed up now...is it something a herculean task to detect correct resolution by a basic OS? why grub, usplash, gdm and gnome session use different resolutions? Why nobody think that this is a problem and it need a simple solution?*

---

### Post by bernardfrancois on 2009-11-14
Hmm,  maybe this is something you could fill a bug report for on ubuntu's launchpad.

For now, to solve your problem, you can edit the xorg.conf file and comment out the resolutions that are too high for your screen.

---

### Post by anishd on 2009-11-14
Thank you Bernard for the reply..I will just try that..I think i will have to add the modelines and all to the xorg.conf as it is almost blank..(Hope that other resolutions-like that of usplash-which were adjusted with much difficulty will not be disturbed by this edit).

Here is my xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by anishd on 2009-11-14
sorry-duplicate post-deleted.

---

### Post by anishd on 2009-11-14
I have edited the xorg.conf file like this..


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
	SubSection "Display"
                Viewport  0 0
                Depth     24
                Modes     "1440x900"
        EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Now the gdm resolution is ok..(although with a few hiccups and bumps, like (1) hearing the gdm sound a few seconds before login screen is displayed, (2) seeing a white screen before logging in after entering password). Thank you..

---

### Post by bernardfrancois on 2009-11-15
Nice to hear that it worked!

Apparently, xorg.conf isn't used any more for setting screen resolution, but it's still possible.
On the following page, there are three methods described on how to add screen resolutions, and modifying xorg.conf is one of them:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

If you look for the title **Setting xrandr commands in kdm/gdm startup scripts**, that's what is probably the best of the three suggested solutions.

I found yet another solution that may solve the problem without the visual artefacts you're talking about:
[http://ubuntuforums.org/showthread.php?t=1308745&highlight=xorg.conf+empty](http://ubuntuforums.org/showthread.php?t=1308745&highlight=xorg.conf+empty)

Please mark the thread as solved if you're happy with the solution:
[http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved](http://ubuntuforums.org/showthread.php?t=524404&highlight=mark+as+solved)

---

### Post by taecha on 2009-12-06
> **bernardfrancois said:**
> 
On the following page, there are three methods described on how to add screen resolutions, and modifying xorg.conf is one of them:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)


I have tried all three methods. While they work, ALL of them occur only after the login?! This causes resizing during the initial screen draw [which is not a big problem] and misplaces items on the panels (e.g., the trash is in the middle of the lower panel and the logout button after the volume, bluethooth, network items).

Does anyone know why and how to solve this?

Thank you.

---

