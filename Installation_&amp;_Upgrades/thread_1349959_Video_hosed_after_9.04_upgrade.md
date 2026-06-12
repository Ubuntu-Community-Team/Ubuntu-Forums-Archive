---
title: "Video hosed after 9.04 upgrade"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by BuntuFreak on 2009-12-08
Hello people. Long time no post.

So I upgraded to Ubuntu 9.04. Then thought I would go to Update Manager and upgrade to 9.10. But wait a sec. Two huge problems.

First, I lost my nVidia Driver. So I'm in 800x600 since my "restricted driver" got trashed. No problem I thought. I'll first upgrade to 9.10 and then try to figure things out. Easier said than done.

I started Update Manager and asked to upgrade to 9.10. What I get is a white square in the middle of the screen. This is supposed to be the window that asks me for the password. But no, I get a white window because something royally messed up with my video.

I go start Terminal. Whatever I type in it, I cannot see. I also start noticing that if I move my mouse slowly it leaves a "square of garbage" behind it as it travels across the screen.

Please tell me I'm not the only one with this problem ](*,)

---

### Post by u.b.u.n.t.u on 2009-12-08
You may be able to log in by removing the xorg.conf file, which the reverts Ubuntu 9.10 back to the default VESA driver.

When starting your computer go to Ubuntu 9.10 recovery mode. At the terminal enter:

rm /etc/X11/xorg.conf

That will delete the file xorg.conf.

Reboot.

---

### Post by BuntuFreak on 2009-12-08
Err... that is not  my problem. my problem is i am unable to see anything in the applications I launch including the Terminal. I cannot see anything i type in the terminal either. So where do i go and fix things assuming someone also tells me how?

---

### Post by u.b.u.n.t.u on 2009-12-08
I am still trying to understand the exact nature of the problem. Rather at a disadvantage by not seeing what you see.

You say you upgrade to 9.04 and then upgraded to 9.10.

So what was the last working version of Ubuntu? Are you able to revert back to that?

---

### Post by BuntuFreak on 2009-12-08
I apologize. First I understand maybe I was not clear. Second, I totally FUBAR 'ed everything.

Let me start over. First of all I have an old desktop with GPU on my motherboard. So I shouldn't need any restricted drivers.

Second, I am able to log on. No confusion there.

Third, I figured out that my "Appearance" was set to Normal on the 9.04 upgrade from Hardy. I changed that to Default and my video glitches went away. I can now see what I type in Terminal.

#-o

The only problem remaining is that I cannot run in resolution higher than 800x600. I used to run at as much as 1600 x 1200 with Hardy. THIS is the only problem I'm left with.

Thanks in advance for your time and help.

P.S. I have not upgraded to 9.10 yet, but I can if it will help.

---

### Post by u.b.u.n.t.u on 2009-12-08
> **BuntuFreak said:**
> I cannot run in resolution higher than 800x600

Does the file xorg.conf exist at the location /etc/X11/ ?

---

### Post by BuntuFreak on 2009-12-09
yes xorg.conf does exist. and it does not have much in it. In fact it has what it would have if i run the command that is there at the end of the comments on the top of the file (how do I know? I backed up and saw what it generated)

upgrading to 9.10 now. let's see what happens. I have an old intel board running a PIII 800 Mhz PC. Methinks Ubuntu will keep on having more and more trouble with older hardware. I had refrained from upgrading from Hardy, but did so accidently. Oh well, not a catastrophe anymore since I can still use it. But it sure is darn ugly.

---

### Post by u.b.u.n.t.u on 2009-12-09
If you could hold off on the upgrade to 9.10 for a moment. I would suggest renaming xorg.conf to something else, reboot, and hopefully you should have your monitor display the correct screen resolution and refresh rate.

---

### Post by BuntuFreak on 2009-12-09
Yikes! Sorry. A little late for that. Should have checked your response today before I did it - already upgraded to 9.10. 

But no worries. I haven't done any more damage. The only perceptible difference I've seen is the login screen was a little black and whitish text instead of weird reddish text.

So do your instructions on renaming xorg.conf and restarting still hold? 

Thanks in advance for your time, patience and expertise.

---------------

UPDATE : Tried deleting xorg.conf. It did not regenerate xorg.conf to fix the problem. So now I've upgraded to 9.10 without any solution to my resolution problem.

---

### Post by BuntuFreak on 2009-12-10
Some more information. I see a file named .xsession-errors in my home folder. Is this relevant and if so, how I can post it to the forum?

Thanks.

---

### Post by u.b.u.n.t.u on 2009-12-10
> **BuntuFreak said:**
> So do your instructions on renaming xorg.conf and restarting still hold?

Removing xorg.conf will revert the GPU driver to the default VESA. One would lose the 3d of the proprietary GPU driver, but it may resolve other issues like limited screen resolutions. Basically a safety net for the GPU.

> **BuntuFreak said:**
> I see a file named .xsession-errors in my home folder. Is this relevant and if so, how I can post it to the forum?

If you have a GPU error, then yes, that would be worth reading.

---

### Post by BuntuFreak on 2009-12-10
Let me paste everything

1) xorg.conf generated using X -configure and modified

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "glx"
	Load  "record"
	Load  "dbe"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

#Section "Monitor"
#	Identifier   "Monitor0"
#	VendorName   "Monitor Vendor"
#	ModelName    "Monitor Model"
#EndSection
Section "Monitor"
	Identifier	"Screen0"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82815 Chipset Graphics Controller (CGC)"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


2) xorg.conf that Ubuntu upgrade left me with

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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


3) .xsession-errors and it does not matter WHAT xorg.conf I use

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-MYaAFv/socket
SSH_AUTH_SOCK=/tmp/keyring-MYaAFv/socket.ssh

(gnome-settings-daemon:1580): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:1580): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Unable to find a synaptics device.
Window manager warning: Failed to read saved session file /home/yoyoma/.config/metacity/sessions/10924446ae14e58a8512605033069736900000014930026.ms: Failed to open file '/home/yoyoma/.config/metacity/sessions/10924446ae14e58a8512605033069736900000014930026.ms': No such file or directory
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/yoyoma/.local/share'

(nautilus:1602): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/yoyoma/.config/tracker/tracker.cfg'
Tracker-Message: Loading defaults into GKeyFile...

(trackerd:1615): GLib-GObject-WARNING **: value "99" of type `gint' is invalid or out of range for property `throttle' of type `gint'
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/yoyoma/.local/share/tracker/data'
Tracker-Message: Checking directory exists:'/home/yoyoma/.cache/tracker'
Failure: Module initalization failed
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/yoyoma/.local/share/tracker/trackerd.log'
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

(polkit-gnome-authentication-agent-1:1619): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1619): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** (gnome-panel:1601): DEBUG: Adding applet 0.
** (gnome-panel:1601): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:1601): DEBUG: Adding applet 1.
** (gnome-panel:1601): DEBUG: Adding applet 2.

** (nautilus:1602): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1602): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1602): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
** (gnome-panel:1601): DEBUG: Adding applet 3.
** (gnome-panel:1601): DEBUG: Adding applet 4.

(gnome-panel:1601): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
** (gnome-panel:1601): DEBUG: Adding applet 5.
** (gnome-panel:1601): DEBUG: Adding applet 6.
** (gnome-panel:1601): DEBUG: Adding applet 7.
** (gnome-panel:1601): DEBUG: Adding applet 8.
** (gnome-panel:1601): DEBUG: Adding applet 9.
** (gnome-panel:1601): DEBUG: Adding applet 10.
** (gnome-panel:1601): DEBUG: Adding applet 11.
** (gnome-panel:1601): DEBUG: Adding applet 12.
** (gnome-panel:1601): DEBUG: Adding applet 13.
evolution-alarm-notify-Message: Setting timeout for 72659 1260576000 1260503341
evolution-alarm-notify-Message:  Fri Dec 11 18:00:00 2009

evolution-alarm-notify-Message:  Thu Dec 10 21:49:01 2009


(gnome-display-properties:1710): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:1710): Gtk-WARNING **: No object called: 

(gnome-display-properties:1726): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:1726): Gtk-WARNING **: No object called: 



Thanks in advance.

---

### Post by u.b.u.n.t.u on 2009-12-11
If there is presently an error, please describe it.

---

### Post by BuntuFreak on 2009-12-11
Other than the .xsession-errors file, there is no obvious error that I can see. I'm still stuck at maximum resolution of 800 x 600 and the "Display" Applet will does not provide me any other option besides 640 X 480.

---

### Post by u.b.u.n.t.u on 2009-12-11
> **BuntuFreak said:**
> Other than the .xsession-errors file, there is no obvious error that I can see. I'm still stuck at maximum resolution of 800 x 600 and the "Display" Applet will does not provide me any other option besides 640 X 480.

I looked through the text and saw no obvious problem. Normally it has something like "error" and the details, but I saw nothing like that.

Well there was "(gnome-settings-daemon:1580): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed", but that is beyond my ability to interpret.

As for the limited screen resolutions, please see if you have the xorg.conf file as I have previously mentioned. If you do have it, renamed it so it is backed up and gone, reboot, and hopefully you will get the correct screen resolution options.

---

### Post by BuntuFreak on 2009-12-11
Sorry, as I said I already tried your option of renaming the xorg.conf to something else and then rebooting it. I'm not sure if the system then is supposed to generate an appropriate xorg.conf file. It certainly didn't do it for me.

Whether I have no xorg.conf file or whether I do, the symptom is the same - stuck in 800 x 600 with no option to go higher. This is really a bummer because when I installed Ubuntu 8.04 and then upgraded to 8.10, it had correctly recognized the capability of my onboard graphics and monitor during install and persisted that on the upgrade.

I accidently hit the upgrade to 9.04 button in Update Manager without realizing it and am rueing it now. It is a good thing I'm running this as a file server. Then again, I cannot handle the downtime of doing the scratch install - which would be my next step. Looking for a hard drive now so I can swap out and experiment, that way if I mess up I'll simply swap the old one back in. It is just so hard to get your hands on a IDE though.

Aaaaaaaarrrrrggggggghhhhhhhhh !

---

### Post by u.b.u.n.t.u on 2009-12-11
> **BuntuFreak said:**
> Sorry, as I said I already tried your option of renaming the xorg.conf to something else and then rebooting it. I'm not sure if the system then is supposed to generate an appropriate xorg.conf file. It certainly didn't do it for me.

At the time of writing a xorg.conf is created one of two ways:

1. installation of proprietary GPU 3d drivers.
2. manual creation.

Removal, if such exist, revert to the default VESA 2d drivers.

> **BuntuFreak said:**
> Whether I have no xorg.conf file or whether I do, the symptom is the same - stuck in 800 x 600 with no option to go higher. This is really a bummer because when I installed Ubuntu 8.04 and then upgraded to 8.10, it had correctly recognized the capability of my onboard graphics and monitor during install and persisted that on the upgrade.

Hopefully this will be rectified by the release of proprietary drivers, updated VESA drivers, or some other updated(s).

Hardware working and not working from version to version is really bad and I have no doubt Ubuntu are aware of this as an urgent matter.

It is clearly the six month release cycles, but such are needed for rapid advancement of Ubuntu. Growing pains, to become fully competitive with Windows 7.

All the best.

---

### Post by BuntuFreak on 2009-12-11
So do you think I have any chances of getting my screen back if I do a scratch install of Ubuntu 9.10? Or should I not bother and simply revert back to Ubuntu 8.10? 

As I said, I'm using it as a file server and not looking for sophisticated features. I plan to swap out the drive with another (my actualy files are on separate drive, heh heh). Just want to know which version I should go with.

Thanks.

---

### Post by u.b.u.n.t.u on 2009-12-11
Ubuntu 9.10 is a mixed bag. It introduces some fine new features but at the same time has trouble with some basics.

If you can, certainly try a fresh install of 9.10. It will only serve to add to your skill and experience level. If all else fails revert to a proven version.

---

