---
title: "Can't play any video files"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-04-17
Totem will not play any video files. I've downloaded the correct drivers. obviously or it wouldn't work at all.

It works perfectly on previous Ubuntu versions, just not Jackalope. I have an integrated Intel video.

Any video file just crashes totem. I used from terminal totem --debug. I got this result:

ubuntu@ubuntu:~$ totem --debug
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by psyke83 on 2009-04-18
Have you made any customizations to your xorg.conf? The "BadAlloc" errors were common for Intel users in conjunction with the XAA acceleration method (though not EXA, which should now be the default).

Check your logs for warnings/errors:
```
$ cat /var/log/Xorg.0.log | grep WW
$ cat /var/log/Xorg.0.log | grep EE
```

A *workaround* you can try is to disable XV output in Gstreamer (and hence Totem):
```
$ gstreamer-properties
```
Video tab, Default Output section. Change the Plugin from "Autodetect" to "X Window System (No Xv)" and close.

I highly suggest you check launchpad for an existing bug regarding your issue (or file a new bug), as this workaround will cause video to be unaccelerated and lower quality than normal.

---

### Post by VMC on 2009-04-18
Thanks for the reply. XORG is untouched. I did notice that xorg.conf is "Valina". reflects just basic info. I tried to replace it with Hardy's xorg.conf and that cased all sorts of problems.

---

### Post by VMC on 2009-04-18
Here's the results of what you suggested:

$ cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB

$ cat /var/log/Xorg.0.log | grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER


What is "cyrillic"? Anything I can do, like? Is there a xorg.conf test.

---

### Post by giruzz on 2009-04-18
> **psyke83 said:**
> Have you made any customizations to your xorg.conf? The "BadAlloc" errors were common for Intel users in conjunction with the XAA acceleration method (though not EXA, which should now be the default).

Check your logs for warnings/errors:
```
$ cat /var/log/Xorg.0.log | grep WW
$ cat /var/log/Xorg.0.log | grep EE
```

A *workaround* you can try is to disable XV output in Gstreamer (and hence Totem):
```
$ gstreamer-properties
```
Video tab, Default Output section. Change the Plugin from "Autodetect" to "X Window System (No Xv)" and close.

I highly suggest you check launchpad for an existing bug regarding your issue (or file a new bug), as this workaround will cause video to be unaccelerated and lower quality than normal.

Same here and the workaround doesn't work :-(

giruzz

---

### Post by VMC on 2009-04-18
I found the problem, but don't know what to do to fix it!

This really isn't a "Jaunty Jackalope" issue, but rather xorg issue. If I had know better I would have placed it in the Multimedia & Video section.

With that said, it first appeared under Jackalope. Hardy didn't have this issue. I guess maybe xorg was updated and some drivers left off.

using the failsafe "vesa" driver will now let me play video files, but only with screen size of 640X480!.
xorg.conf using vesa:
...
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"[COLOR="Red"]vesa[/COLOR]"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Screen size correct but can't play video:
xorg.conf
...
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

[COLOR="Red"]**How do I get the correct driver for my integrated Intel G865**[/COLOR]??? Here's snapshot of xorg.conf running under Hardy that worked:
...
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"Intel 865"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

---

### Post by VMC on 2009-04-18
After reading a post on Multimedia & Video, I found that xserver-xorg-video- in Synaptic shows a intel driver installed.

So I used intel in xorg.conf:
...
Section "Device"
Identifier "Configured Video Device"
Driver "intel"
EndSection

When I used that, I get 1024X768 but still I can't play video movies. I wonder what the vesa driver does that the intel driver doesn't do that allows for playing video?

---

### Post by VMC on 2009-04-21
Problem solved. If you have video issues you might want to check out this [LINK]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4"). It completely fixed my video issues.

---

### Post by stewacide on 2009-04-21
I had the same problem (it's not just Totem, VLC and every other player I tried would crash, in addition to terrible flash performance and broken compiz).

The first solution I found was what you've done: revert to the 2.4 drivers. However a better (as in better-performing) solution is this: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

If it doesn't work for ya' it's quick and easy to go back to the 2.4 config with the jaunty kernel.

---

