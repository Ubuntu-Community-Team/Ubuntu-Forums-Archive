---
title: "Upgrade from Feisty to Gusty destroyed everything I know and love..."
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by El Lance-O on 2007-11-25
So I have put off upgrading to Gutsy until now, and I wish I had longer.

While upgrading there were SEVERAL errors about dependencies not being met and replacements of files. Most of the replacements I accepted, except for the one that said would render my nvidia card useless.

I took screenshots of each error as it went along (I must stress, there were A LOT) but now when I boot, it tells me X was killed in the update.

Here is the only info I can gather at this point:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux TheThinGreyBox 2.6.20-16-generic #2 SMP Fri Aug 31 00:55:27 UTC 2007 i686
Build Date: 29 September 2007
          Before reporting problems, check http://wiki.x.org
          to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
           (++) from command line, (!!) notice, (II) informational,
           (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Nov 25 13:53:33 2007
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in

```

It then asks me if I was to view the detailed X server output as well, which is the same as the last except for these lines are under the "(==) Using config file: "/etc/X11/xorg.conf" part:

```
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |    |-->Monitor "Generic Monitor"
```

Then it says: "The X server is now disabled. Restart GDM when it is configured correctly."

Then it just hangs at the list of things starting at boot after "*Running local boot scripts"

I am so very upset right now I don't even know where to begin. I just was starting to think I had everything down perfect, and then it all gets ravaged by this unfortunate event.

I am running on a Dell Inspiron 1505n. I came preloaded with Feisty, and I was hoping this would mean nothing like this sort of thing would happen.

I guess I was absolutely wrong for ever putting trust into Dell, or Ubuntu for that matter.

I am utterly devastated and disappointed at how badly this has turned out. I may even be giving up on Ubuntu if this cannot be resolved. I hate to have to go back to Windows, but this is ridiculous. I just lost everything, including my midterms which is kind of vital right now at this point in my life.

Please someone tell me there is some kind of recovery process to fix this or at least salvage files off of my hard drive.

Please someone help ASAP, this laptop is my life, and I'd hate to see it turned into nothing more but a paperweight. :(

---

### Post by babygigi on 2007-11-25
You can use a live cd to get into your computer inorder to retrieve your files. I know how it feels, mine crashed from edgy to fiesty. There are many posts around regarding the retrevial of files.

---

### Post by rsambuca on 2007-11-25
You can use any liveCD and retrieve your files to a thumbdrive.

Yes, there have been problems with upgrades, but ones of this extreme nature are fairly rare.  Have you used many repositories outside the standard repositories?  Have you used any external scripts or programs to install things, such as automatix, etc?  Do you not back up your data?

---

### Post by El Lance-O on 2007-11-25
Well I fixed the X problem without breaking a sweat. I went to the Dell Linux Wiki and found this:

```

Description: The Gnome Display Manager does not start after upgrading from Ubuntu 7.04 to Ubuntu 7.10.
Systems Affected: Inspiron 1420n
Impact: The X window manager (Gnome Display Manager) will not start.
Fix: Switch to virtual terminal 1 by typing Ctrl+Alt+F1 and run:

$sudo dpkg-reconfigure -fnoninteractive xserver-xorg

followed by a reboot.

This command will configure the system to use the correct video driver in /etc/X11/xorg.conf. 
```|

I did that and booted back onto my desktop no problem. I had to enable a restricted nvidia driver, but nothing seemed too bad other than the grey screen on boot instead of the default tan.

Oh....wait nevermind. It just popped up with another X error. Fantastic...
Everything is the same up to:
> (II) Module already built-in

But now I have:

> Error: API mismatch: the NVIDIA kernel module has the version 1.0-9631, but
this X module has the version 1.0-9639.   Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):      that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):      that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):      Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** ABORTING ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

I hope I never have to deal with this again....

---

### Post by gpilkay on 2007-11-25
I understand perfectly.  An aborted 7.10 install killed a notebook for me, too.

What you can do is use the 7.10 CD (It seems to work better for laptops in general) and boot to it.  Then copy off all your info to any USB thumb drive or the like.  After that, a fresh install might be in order, but first thing's first:  Back up the data.

I have a Dell Vostro with Windows XP.  After the Ubuntu problem, I use the pre-installed XP, but use the live-CD as a separate thing when I need Linux on the road.  For my actual install, I keep Ubuntu on my duel-hard drive desktop.  I'm not upgrading till the semester's over, though (I'm a grad student).

---

### Post by El Lance-O on 2007-11-25
> **rsambuca said:**
> You can use any liveCD and retrieve your files to a thumbdrive.

Yes, there have been problems with upgrades, but ones of this extreme nature are fairly rare.  Have you used many repositories outside the standard repositories?  Have you used any external scripts or programs to install things, such as automatix, etc?  Do you not back up your data?

I never used Automatix (who in their right mind would?) and I have MAYBE 4 repositories other than the standard. All are trustworthy and well known.

I don't back up anything, as this is the only computer I own at the moment. I am on a friends laptop (also running Gutsy, with no problem....*******) doing all of this, but I have no means of transferring data from mine to this one.

---

### Post by El Lance-O on 2007-11-25
> **gpilkay said:**
> I understand perfectly.  An aborted 7.10 install killed a notebook for me, too.

What you can do is use the 7.10 CD (It seems to work better for laptops in general) and boot to it.  Then copy off all your info to any USB thumb drive or the like.  After that, a fresh install might be in order, but first thing's first:  Back up the data.

I have a Dell Vostro with Windows XP.  After the Ubuntu problem, I use the pre-installed XP, but use the live-CD as a separate thing when I need Linux on the road.  For my actual install, I keep Ubuntu on my duel-hard drive desktop.  I'm not upgrading till the semester's over, though (I'm a grad student).

I was going to do this originally, but it would take me FOREVER to back up everything even if I had the means to do so. I have probably around 40 gigs of stuff that I consider important, not to mention the DAYS of configuring everything to how I see fit.

This is the last thing I want to do, trust me.

---

### Post by El Lance-O on 2007-11-25
Update: I can freely boot into my desktop now after using the command from the Dell Ubuntu Wiki. But I still cannot enable the nvidia restricted driver.

And I have noticed my wireless no longer works. It says it is connected, but what do you know, nothing happens in my browser or otherwise.

This is getting so incredibly frustrating. I cannot find a single shred of help on this, and believe me, I have been doing nothing but searching this whole time.

Can someone shed any light on this? Anyone? At all?

Update: Well I got my wireless to work again. I read this in the Gutsy release notes:

```
In Ubuntu 7.10, network-manager only manages interfaces that are marked for roaming.
Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade.
Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces.
If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network.
```

I assumed this might be why it wasn't working, so I manually configured it, rebooted, and it works fine now.

I also was looking though all the screenshots of the packages that didn't install because of dependency problems or otherwise. The list is as follows:

```
bluez-utils
linux-sound-base
asla-utils
alsa-base
ubuntu-minimal
gdm
fast-user-switch-applet
ubuntu-desktop
```

I also noticed the last screenshot I took:

[IMG]http://img160.imageshack.us/img160/5432/screenshotgutsy3ua3.png[/IMG]

So of course I tried 'dpkg --configure -a', which gave me this:

```
ellanceo@TheThinGreyBox:~$ sudo dpkg --configure -a
Setting up bluez-utils (3.19-0ubuntu3) ...
dpkg: error processing bluez-utils (--configure):
 subprocess post-installation script returned error exit status 3
Setting up linux-sound-base (1.0.14-1ubuntu2) ...
Error: the current /etc/modules.conf is not automatically generated.
Use "update-modules force" to force (re)generation.
dpkg: error processing linux-sound-base (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of alsa-utils:
 alsa-utils depends on linux-sound-base (>= 1.0.11-2); however:
  Package linux-sound-base is not configured yet.
dpkg: error processing alsa-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alsa-base:
 alsa-base depends on linux-sound-base; however:
  Package linux-sound-base is not configured yet.
dpkg: error processing alsa-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on alsa-base; however:
  Package alsa-base is not configured yet.
 ubuntu-minimal depends on alsa-utils; however:
  Package alsa-utils is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on alsa-utils; however:
  Package alsa-utils is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on fast-user-switch-applet; however:
  Package fast-user-switch-applet is not configured yet.
 ubuntu-desktop depends on gdm; however:
  Package gdm is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bluez-utils
 linux-sound-base
 alsa-utils
 alsa-base
 ubuntu-minimal
 gdm
 fast-user-switch-applet
 ubuntu-desktop
```

I also read somewhere that someone's nvidia restricted drivers wouldn't install because they weren't connected to the internet. So I am gonna give that a try now that I have fixed my network, and we'll see what happens.

Update: OK, so that didn't work, so I searched about the API mismatch, which lead me to a post with instructions to reinstall nvidia-glx because of the kernel version discrepancy. I did this and now it added nvidia-kernel-common, nvidia-glx, and linux-restricted-modules-2.6.22-14-386 to the list of packages with dependency problems.

The error itself is:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've looked at other threads about this, but none of them seem to have an answer.

So what is up with these dependency problems? That seems to be the source of all this evil.

---

### Post by El Lance-O on 2007-11-25
Read updates ^

---

### Post by El Lance-O on 2007-11-25
Come on, there has to be SOMETHING someone can tell me!

I can't only repost in my own thread so many times.

I've figured out most of this on my own, but no matter how hard I look I cannot get a straight answer with the dependency problem.

PLEASE HELP.

I assume this will fix just about all my problems right now.

---

### Post by El Lance-O on 2007-11-25
Oh, and now my ath0 completely disappeared. Probably because linux-restricted-modules is screwed up. Therefore my internet no longer works, and now it makes this A LOT harder.

For the love of Canonical, will someone please help me so I can stop looking like an annoying poster and get on with my life already?

---

### Post by nzadLithium on 2007-11-25
for all your dependency issues you could try going into synatpic and checking reinstall on all of those ones. I think that will fix all  the depdency stuff. You will need the internet for that though.

What were you doing when ath0 dissapeared? And what is ath0 im assuming its a network device? maybe you meant eth0?
can you still get into the Network program? If so can you check that all the devices are setup properly?

Post the output of dmesg (type into terminal)

and run 
sudo update-modules force
as was suggested by the dpkg. see if your net goes after that. 

From the output of ur reconfigure im thinking that everything is not working only because of the alsa packages. I think if you reinstall all those packages it will work.

That line your calling an error from dmesg is not really an error (well not a proper one) its just saying it encountered an error which could be a number of things.

I dont no if any of this will fix your Nvidia driver problems though that could be entirely something else. Just do the other stuff concentrate on getting your net and those other packages installed properly first.

---

### Post by El Lance-O on 2007-11-25
Ok, the dependency problem solved itself somehow, as the packages are installed with no problem.

Now the problem I have is that when I was messing around with the linux-restricted-driver nonsense, it totally screwed up my nvidia card.

So the new kernel should be 2.6.22-14 right? Well it's in my /boot folder, but it keeps giving me an Error 15: File Not Found when trying to boot into it.

So I'm stuck with booting into 2.6.20-16, and the problem I was having was that I couldn't enable the restricted drivers because the 2.6.22-14 one was installed.

I burned a CD with the right package, installed it, and installed nvidia-glx-new, amongst other nvidia packages, and now when I start, it starts in low graphic mode and says it can't detect the kind of display I have.

I search through the list and can't find something that will let me run with my native resolution: 1280x800.

So again, I am stumped. So....SO...incredibly sick and tired of dealing with this, and I just wish it never happened.

Thank you so much for being the one person to respond after all this time.

I just hope I can get this resolved soon.

THIS THREAD IS NOT DONE, EXPECT TO SEE IT MORE OFTEN, WE CANNOT ALLOW SOMETHING LIKE THIS TO HAPPEN AGAIN WITHOUT RESOLVE.

Thank you again, I will try again tomorrow.

---

### Post by nzadLithium on 2007-11-26
is it booting the new kernel now?? if not then go into synaptic package manager and try reinstalling the new kernel.
I'm not sure what happens in low graphics mode so if you don't have a GUI then I'll have to find out how to reinstall the kernel using terminal commands.

That low graphics thing could be being caused by an incorrectly setup / corrupted xorg.conf file.
run this in a terminal.

gksudo gedit /etc/X11/xorg.conf

Don't touch the contents of the file unless you know what your doing.

copy and paste it here and i'll have a look at it. 

And plz once you have freshly started up the pc and logged in can you post the output of dmesg + the log from xorg? to get it goto system, administration, system log then click xorg log on the left side.

I guess i know how you feel. Linux is great but i get a bit annoyed when these kinda set backs occur. I had problems with me being stupid and installing conflicting nvidia drivers the first time i installed Linux on this PC. I have most of my hardware going now. I haven't tried the scanner though, theres no drivers for my webcam and it seems the new versions of LIRC broke support for my remote control so i have to go find an old version that works some time :S I'm slowly getting everything to go though but it looks like I'm going to have to learn how to write drivers to get my webcam going. I know a little programming but i dont think i know enough to do anything that low level (im only just getting into gui's). The webcams fairly old (2000 i think) so if it comes to that maybe the manufacturer will be nice and give me any specs i need to write a driver. :S

Sorry for not shutting up about me. I seem to have a problem with not being able to shut up :D

---

### Post by nzadLithium on 2007-11-26
I'm not sure what the latest ubuntu linux kernel is. The latest stable linux kernel is 2.6.23.9 but it takes a bit of time for distros to get an update setup. The latest fairly stable version is 2.6.24-rc3 I want that one! it has a cool rc3 on the end :D

I think seriously that the latest kernel in repositories would be 2.6.22.* like you said earlier although i cant check coz i havent done the upgrade myself yet. Gona do end of the month if i remember. I need to for my other computer running ati so i can get the latest drivers going and hopefully get some decent in game 3D accell.

---

### Post by mikewhatever on 2007-11-26
Wow El Lance-O, you are dramatic. Judging by the title of the thread I expected the story of you driven to the icy wilderness (Alaska), your house demolished and the whole town burnt down, your family and friends murdered and possessions looted, and all that by upgrading to Gutsy Gibbon (the evil?). Imagine the disappointment when I saw that all you had was a broken upgrade. I was almost ready to donate, and now ... :-(.

---

### Post by El Lance-O on 2007-11-26
Haha, don't worry about it, we all have to vent sometime. I mean just look at the majority of my posts in these threads.

Anyways, the internet thing was my mistake, it was eth0 not ath0. My bad.

It was fixed when installed the linux-restricted-module package for 2.6.20-16.

Anyways, I know the problem HAS to be with my xorg.conf, because it is clearly different. I tried replacing it with the old one, but it just changes back. I don't get it...

Anyways, here's the old one from a couple months back:

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
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
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

And the new one:

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
	Identifier	"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x800"
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

The only difference is that it says it was generated by xconfig, but I never used that. I just copied and pasted the old one and it won't work.

I just don't get it.

Oh, and here's the output of dmesg:

```
[   23.870386] Enabling unmasked SIMD FPU exception support... done.
[   23.870393] Initializing CPU#0
[   23.870460] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   23.872969] Console: colour VGA+ 80x25
[   23.873268] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   23.873660] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.898940] Memory: 1027188k/1047372k available (1993k kernel code, 19472k reserved, 900k data, 328k init, 129868k highmem)
[   23.898949] virtual kernel memory layout:
[   23.898950]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.898952]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.898953]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   23.898954]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   23.898956]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   23.898957]       .data : 0xc02f2434 - 0xc03d36d4   ( 900 kB)
[   23.898958]       .text : 0xc0100000 - 0xc02f2434   (1993 kB)
[   23.898962] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.899118] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   23.899123] hpet0: 3 64-bit timers, 14318180 Hz
[   23.900129] Using HPET for base-timer
[   23.979089] Calibrating delay using timer specific routine.. 3461.94 BogoMIPS (lpj=6923884)
[   23.979132] Security Framework v1.0.0 initialized
[   23.979141] SELinux:  Disabled at boot.
[   23.979157] Mount-cache hash table entries: 512
[   23.979298] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   23.979307] monitor/mwait feature present.
[   23.979309] using mwait in idle threads.
[   23.979313] CPU: L1 I cache: 32K, L1 D cache: 32K
[   23.979316] CPU: L2 cache: 1024K
[   23.979318] CPU: Physical Processor ID: 0
[   23.979320] CPU: Processor Core ID: 0
[   23.979322] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   23.979332] Compat vDSO mapped to ffffe000.
[   23.979336] Remapping vsyscall page to ffffe000
[   23.979348] Checking 'hlt' instruction... OK.
[   23.995195] SMP alternatives: switching to UP code
[   23.995576] Early unpacking initramfs... done
[   24.317912] ACPI: Core revision 20060707
[   24.334383] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   24.337089] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[   24.337110] SMP alternatives: switching to SMP code
[   24.337239] Booting processor 1/1 eip 3000
[   26.642178] Initializing CPU#1
[   26.719374] Calibrating delay using timer specific routine.. 3458.09 BogoMIPS (lpj=6916198)
[   26.719381] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   26.719386] monitor/mwait feature present.
[   26.719389] CPU: L1 I cache: 32K, L1 D cache: 32K
[   26.719391] CPU: L2 cache: 1024K
[   26.719394] CPU: Physical Processor ID: 0
[   26.719395] CPU: Processor Core ID: 1
[   26.719397] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   24.427255] CPU1: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[   24.427278] Total of 2 processors activated (6920.04 BogoMIPS).
[   24.427481] ENABLING IO-APIC IRQs
[   24.427684] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   24.574840] checking TSC synchronization across 2 CPUs: 
[    0.000002] CPU#0 had -1146720 usecs TSC skew, fixed it up.
[    0.000004] CPU#1 had 1146720 usecs TSC skew, fixed it up.
[    0.003997] Brought up 2 CPUs
[    0.074030] migration_cost=50
[    0.074313] Booting paravirtualized kernel on bare hardware
[    0.074403] Time: 11:59:53  Date: 10/26/107
[    0.074432] NET: Registered protocol family 16
[    0.074517] EISA bus registered
[    0.074521] ACPI: bus type pci registered
[    0.103395] PCI: PCI BIOS revision 2.10 entry at 0xfb336, last bus=13
[    0.103397] PCI: Using configuration type 1
[    0.103399] Setting up standard PCI resources
[    0.131163] ACPI: Interpreter enabled
[    0.131166] ACPI: Using IOAPIC for interrupt routing
[    0.132111] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.132119] PCI: Probing PCI hardware (bus 00)
[    0.132315] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[    0.146480] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.146485] PCI quirk: region 1080-10bf claimed by ICH6 GPIO
[    0.146713] Boot video device is 0000:01:00.0
[    0.147738] PCI: Transparent bridge - 0000:00:1e.0
[    0.147812] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.168949] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *4
[    0.169214] ACPI: PCI Interrupt Link [LNKB] (IRQs *5 7)
[    0.169477] ACPI: PCI Interrupt Link [LNKC] (IRQs *9 10 11)
[    0.169740] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 11) *3
[    0.170006] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.170278] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.170544] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.170810] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.171268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.172430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.172707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.173121] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.173572] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.173583] pnp: PnP ACPI init
[    0.207708] pnp: PnP ACPI: found 12 devices
[    0.207712] PnPBIOS: Disabled by ACPI PNP
[    0.207762] PCI: Using ACPI for IRQ routing
[    0.207765] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.255229] NET: Registered protocol family 8
[    0.255232] NET: Registered protocol family 20
[    0.274515] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.274518] pnp: 00:02: ioport range 0x1000-0x1005 could not be reserved
[    0.274521] pnp: 00:02: ioport range 0x1008-0x100f could not be reserved
[    0.274527] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.274530] pnp: 00:03: ioport range 0x1006-0x1007 has been reserved
[    0.274533] pnp: 00:03: ioport range 0x100a-0x1059 could not be reserved
[    0.274536] pnp: 00:03: ioport range 0x1060-0x107f has been reserved
[    0.274538] pnp: 00:03: ioport range 0x1080-0x10bf has been reserved
[    0.274541] pnp: 00:03: ioport range 0x10c0-0x10df has been reserved
[    0.274548] pnp: 00:08: ioport range 0xc80-0xcff could not be reserved
[    0.274551] pnp: 00:08: ioport range 0x910-0x91f has been reserved
[    0.274554] pnp: 00:08: ioport range 0x920-0x92f has been reserved
[    0.274556] pnp: 00:08: ioport range 0xcb0-0xcbf has been reserved
[    0.274559] pnp: 00:08: ioport range 0x930-0x97f has been reserved
[    0.274859] PCI: Bridge: 0000:00:01.0
[    0.274860]   IO window: disabled.
[    0.274865]   MEM window: ed000000-efefffff
[    0.274868]   PREFETCH window: d0000000-dfffffff
[    0.274872] PCI: Bridge: 0000:00:1c.0
[    0.274874]   IO window: disabled.
[    0.274880]   MEM window: ecf00000-ecffffff
[    0.274884]   PREFETCH window: disabled.
[    0.274890] PCI: Bridge: 0000:00:1c.3
[    0.274894]   IO window: e000-efff
[    0.274900]   MEM window: ecc00000-ecefffff
[    0.274905]   PREFETCH window: e0000000-e01fffff
[    0.274912] PCI: Bridge: 0000:00:1e.0
[    0.274913]   IO window: disabled.
[    0.274919]   MEM window: ecb00000-ecbfffff
[    0.274924]   PREFETCH window: disabled.
[    0.274943] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.274949] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.274972] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.274978] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.275003] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    0.275009] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.275024] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.275056] NET: Registered protocol family 2
[    0.319919] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.320043] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.320755] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.321130] TCP: Hash tables configured (established 131072 bind 65536)
[    0.321134] TCP reno registered
[    0.336001] checking if image is initramfs... it is
[    0.975405] Freeing initrd memory: 6746k freed
[    0.975599] Simple Boot Flag at 0x79 set to 0x1
[    0.976070] audit: initializing netlink socket (disabled)
[    0.976088] audit(1196078394.736:1): initialized
[    0.976185] highmem bounce pool size: 64 pages
[    0.976275] VFS: Disk quotas dquot_6.5.1
[    0.976296] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.976344] io scheduler noop registered
[    0.976347] io scheduler anticipatory registered
[    0.976349] io scheduler deadline registered
[    0.976362] io scheduler cfq registered (default)
[    0.976613] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.976651] assign_interrupt_mode Found MSI capability
[    0.976654] Allocate Port Service[0000:00:01.0:pcie00]
[    0.976746] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.976805] assign_interrupt_mode Found MSI capability
[    0.976808] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.976842] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.976966] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.977026] assign_interrupt_mode Found MSI capability
[    0.977029] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.977061] Allocate Port Service[0000:00:1c.3:pcie02]
[    0.977241] isapnp: Scanning for PnP cards...
[    1.331698] isapnp: No Plug & Play device found
[    1.359534] Real Time Clock Driver v1.12ac
[    1.359596] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.360327] mice: PS/2 mouse device common for all mice
[    1.360869] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.361100] input: Macintosh mouse button emulation as /class/input/input0
[    1.361134] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.361138] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.361389] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.364449] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.364453] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.364574] EISA: Probing bus 0 at eisa.0
[    1.364586] Cannot allocate resource for EISA slot 1
[    1.364617] EISA: Detected 0 cards.
[    1.394801] TCP cubic registered
[    1.394812] NET: Registered protocol family 1
[    1.394838] Starting balanced_irq
[    1.394845] Using IPI No-Shortcut mode
[    1.394976] ACPI: (supports S0 S3 S4 S5)
[    1.395022]   Magic number: 15:592:985
[    1.395315] Freeing unused kernel memory: 328k freed
[    1.395412] Time: tsc clocksource has been installed.
[    1.396200] input: AT Translated Set 2 keyboard as /class/input/input1
[    2.602269] Capability LSM initialized
[    2.642390] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[    2.642576] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[    2.642791] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    2.642797] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.643299] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[    2.643468] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[    2.643725] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    2.643730] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.224000] ACPI: Thermal Zone [THM] (25 C)
[    3.228000] Time: hpet clocksource has been installed.
[    3.616000] usbcore: registered new interface driver usbfs
[    3.616000] usbcore: registered new interface driver hub
[    3.616000] usbcore: registered new device driver usb
[    3.616000] USB Universal Host Controller Interface driver v3.0
[    3.616000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 18
[    3.616000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.616000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.616000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.616000] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000bf80
[    3.616000] usb usb1: configuration #1 chosen from 1 choice
[    3.616000] hub 1-0:1.0: USB hub found
[    3.616000] hub 1-0:1.0: 2 ports detected
[    3.700000] ieee1394: Initialized config rom entry `ip1394'
[    3.720000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 19
[    3.720000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.720000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.720000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.720000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000bf60
[    3.720000] usb usb2: configuration #1 chosen from 1 choice
[    3.720000] hub 2-0:1.0: USB hub found
[    3.720000] hub 2-0:1.0: 2 ports detected
[    3.824000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 20
[    3.824000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.824000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.824000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.824000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000bf40
[    3.824000] usb usb3: configuration #1 chosen from 1 choice
[    3.824000] hub 3-0:1.0: USB hub found
[    3.824000] hub 3-0:1.0: 2 ports detected
[    3.928000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 21
[    3.928000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.928000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.928000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.928000] uhci_hcd 0000:00:1d.3: irq 21, io base 0x0000bf20
[    3.928000] usb usb4: configuration #1 chosen from 1 choice
[    3.928000] hub 4-0:1.0: USB hub found
[    3.928000] hub 4-0:1.0: 2 ports detected
[    4.032000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 18
[    4.032000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.032000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.032000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.032000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.032000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.032000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xffa80000
[    4.036000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.036000] usb usb5: configuration #1 chosen from 1 choice
[    4.036000] hub 5-0:1.0: USB hub found
[    4.036000] hub 5-0:1.0: 8 ports detected
[    4.036000] SCSI subsystem initialized
[    4.044000] libata version 2.20 loaded.
[    4.140000] ata_piix 0000:00:1f.2: version 2.10ac1
[    4.140000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.140000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 22
[    4.140000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.140000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001bfa0 irq 14
[    4.140000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001bfa8 irq 15
[    4.140000] scsi0 : ata_piix
[    4.304000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.304000] ata1.00: ATA-7: SAMSUNG HM080HI, AB100-12, max UDMA/100
[    4.304000] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    4.312000] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
[    4.312000] ata1.00: configured for UDMA/100
[    4.312000] scsi1 : ata_piix
[    4.632000] ata2.00: ATAPI, max UDMA/33
[    4.796000] ata2.00: configured for UDMA/33
[    4.796000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM080HI  AB10 PQ: 0 ANSI: 5
[    4.800000] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-T11N A103 PQ: 0 ANSI: 5
[    4.800000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 17
[    4.852000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[ecbfd800-ecbfdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.860000] b44.c:v1.01 (Jun 16, 2006)
[    4.860000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
[    4.860000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:7c:2e:2a
[    4.864000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.864000] sda: Write Protect is off
[    4.864000] sda: Mode Sense: 00 3a 00 00
[    4.864000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.864000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[    4.864000] sda: Write Protect is off
[    4.864000] sda: Mode Sense: 00 3a 00 00
[    4.864000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.864000]  sda:sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.872000] Uniform CD-ROM driver Revision: 3.20
[    4.872000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.876000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.876000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    5.720000]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[    5.748000] sd 0:0:0:0: Attached scsi disk sda
[    6.104000] Attempting manual resume
[    6.104000] swsusp: Resume From Partition 8:5
[    6.104000] PM: Checking swsusp image.
[    6.108000] PM: Resume from disk failed.
[    6.128000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[364fc00035790981]
[    6.180000] kjournald starting.  Commit interval 5 seconds
[    6.180000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.140000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   13.292000] Netfilter messages via NETLINK v0.30.
[   13.304000] nf_conntrack version 0.5.0 (8182 buckets, 65456 max)
[   14.840000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.844000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.988000] iTCO_vendor_support: vendor-support=0
[   15.000000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.000000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.000000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.100000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.120000] intel_rng: FWH not detected
[   15.152000] agpgart: Detected an Intel 945GM Chipset.
[   15.172000] agpgart: AGP aperture is 256M @ 0x0
[   15.216000] sdhci: Secure Digital Host Controller Interface driver
[   15.216000] sdhci: Copyright(c) Pierre Ossman
[   15.216000] sdhci: SDHCI controller found at 0000:03:01.1 [1180:0822] (rev 19)
[   15.216000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   15.216000] mmc0: SDHCI at 0xecbfd400 irq 23 DMA
[   15.336000] ieee80211_crypt: registered algorithm 'NULL'
[   15.348000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.348000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.464000] input: PC Speaker as /class/input/input2
[   15.524000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   15.524000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   15.524000] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.524000] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[   15.524000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   15.668000] mmcblk0: mmc0:db12 SD01G 1006080KiB 
[   15.668000]  mmcblk0: p1
[   15.920000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 19
[   15.920000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.924000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   15.960000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   16.504000] lp: driver loaded but no devices found
[   16.560000] fuse init (API version 7.8)
[   16.588000] Adding 1301224k swap on /dev/sda5.  Priority:-1 extents:1 across:1301224k
[   17.464000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   17.508000] EXT3 FS on sda6, internal journal
[   18.240000] kjournald starting.  Commit interval 5 seconds
[   18.240000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   18.248000] EXT3 FS on sda3, internal journal
[   18.248000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.308000] PPP generic driver version 2.4.2
[   19.336000] NET: Registered protocol family 17
[   19.396000] NET: Registered protocol family 10
[   19.396000] lo: Disabled Privacy Extensions
[   19.396000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.396000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   19.440000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   29.484000] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[   29.560000] usbcore: registered new interface driver hsfusbcd2
[   29.656000] ACPI: AC Adapter [AC] (on-line)
[   29.724000] ACPI: Battery Slot [BAT0] (battery present)
[   29.740000] input: Lid Switch as /class/input/input4
[   29.740000] ACPI: Lid Switch [LID]
[   29.740000] input: Power Button (CM) as /class/input/input5
[   29.740000] ACPI: Power Button (CM) [PBTN]
[   29.740000] input: Sleep Button (CM) as /class/input/input6
[   29.740000] ACPI: Sleep Button (CM) [SBTN]
[   29.796000] Using specific hotkey driver
[   29.848000] No dock devices found.
[   29.896000] ibm_acpi: ec object not found
[   30.016000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   30.020000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   30.020000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   30.048000] pcc_acpi: loading...
[   30.400000] eth1: no IPv6 routers present
[   33.180000] ppdev: user-space parallel port driver
[   33.776000] apm: BIOS not found.
[   36.992000] Capability LSM initialized
[   94.924000] UDF-fs: No VRS found
[   94.944000] ISO 9660 Extensions: Microsoft Joliet Level 3
[   94.952000] ISO 9660 Extensions: RRIP_1991A
[   95.596000] FAT: Unrecognized mount option "usefree" or missing value
[  168.056000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=44691 PROTO=UDP SPT=138 DPT=138 LEN=224 
[  545.176000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=44725 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 1067.928000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=44726 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 1262.112000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=44727 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 1967.800000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=59020 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 1982.072000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=59427 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 1997.136000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=59601 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1997.884000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=59686 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 1998.636000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=78 TOS=0x00 PREC=0x00 TTL=128 ID=59718 PROTO=UDP SPT=137 DPT=137 LEN=58 
[ 2704.596000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=27401 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 2867.660000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=29909 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 3426.616000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=36807 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 3767.528000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=37872 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 4149.192000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=37958 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 4667.408000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=45210 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 4868.416000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=45369 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 5567.276000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=46067 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 5589.388000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=46070 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 6307.096000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=55601 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 6467.144000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=56693 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 7028.528000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=59871 PROTO=UDP SPT=138 DPT=138 LEN=216 
[ 7367.040000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=244 TOS=0x00 PREC=0x00 TTL=128 ID=61518 PROTO=UDP SPT=138 DPT=138 LEN=224 
[ 7748.416000] Inbound IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0c:41:e6:c5:cd:08:00 SRC=192.168.1.2 DST=192.168.1.255 LEN=236 TOS=0x00 PREC=0x00 TTL=128 ID=63951 PROTO=UDP SPT=138 DPT=138 LEN=216 
```

---

### Post by BlinkyB on 2007-11-26
I had many problems with the Gutsy install using my NVIDIA 6600GT and BenQ LCD which I've now finally resolved or worked around.

First, the normal installation tried to start up X and left my monitor saying "Out of Range". So I reverted to the text based installation. This seemed to run fine but then I couldn't start X at all (except for the very unpleasant VGA failsafe mode). I installed the latest NVIDIA driver and could then start X from a "Recovery" boot (single user) and then /etc/init.d/gdm start, Running a normal boot left the monitor with "Out of Range" again.

So I finally discovered that the system couldn't detect the monitor scan frequency ranges. (This always worked before...) So I looked them up and plugged them into the xorg.conf.

Still no good. Booting up normally resulting in the nvidia module not being loaded or not loaded properly or the wrong module being loaded. I found I had to HACK the gdm startup script to "rmmod nvidia" then "modprobe nvidia" before starting gdm.

This now work properly. At long last.

This was quite a horrible problem and took many hours of work to find the fix - if you can call it a fix. Really disappointed that the default Ubuntu installation couldn't work out my monitor parameters and load the nvidia driver properly.

---

### Post by nzadLithium on 2007-11-26
are we still having the low graphics problem because that xorg seems to be setup fine as long as you dont call 1280 x 1024 resolution low.

It must have loaded the drivers because there are no error outputs about them so its either something the driver has a problem with or that the xserver has a problem with. I think both of those cases would be reported in the xorg log which i mentioned how to get to earlier.

did u reinstall the latest kernel yet? Have you tried it to see if it loads? do the graphics work fine with that kernel?

---

### Post by El Lance-O on 2007-11-27
> **mikewhatever said:**
> Wow El Lance-O, you are dramatic. Judging by the title of the thread I expected the story of you driven to the icy wilderness (Alaska), your house demolished and the whole town burnt down, your family and friends murdered and possessions looted, and all that by upgrading to Gutsy Gibbon (the evil?). Imagine the disappointment when I saw that all you had was a broken upgrade. I was almost ready to donate, and now ... :-(.

Hahaha, yes I will admit this was a TAD dramatic, and nothing compared to anything else that could happen to me, but this laptop really is a large aspect of my life, as materialistic and sad that is. Although if all of that would to occur, that would be quite ironic indeed.

As for you not wanting to give any input on the matter because I was a little over-reactive with the thread title, so be it. Really shows how much you ACTUALLY care about the whole community aspect of Ubuntu. :popcorn:

As for the kernel, no I have not tried doing any of that yet, but I will do that here in about two seconds. I forgot that while it may show up in my GRUB menu, I do have a Dell preloaded laptop, which means they separately partitioned my boot files, which I totally forgot about until just now.

AH HA!

I will update as soon as I figure anything out.

---

### Post by El Lance-O on 2007-11-27
Alright, the problem is as follows (or so it seems):

Since my boot files are located on a separate partition as updated with linux-headers, I used to have to edit the GRUB menu at each start-up from (0,2) to (0,5). But when I try and mount the 'OS' partition, I get this:

[IMG]http://img526.imageshack.us/img526/2548/screenshotgnomemountjf4.png[/IMG]

I found this with dmesg | tail:

```
[ 2398.676000] FAT: Unrecognized mount option "usefree" or missing value
```

So since I cannot mount that partition, I assume when I try and install the new kernel, it cannot create symlinks in /boot.

At least it said something to that extent under the 'Details' while reinstalling in Synaptic like you suggested.

What to do now?

Oh and I also fixed the problem with the resolution, but it's not all fixed completely. I went to go enable the nvidia restricted driver, when it starts downloading the 2.6.22-14 kernel for 386. I noticed there was a 386 entry on the grub menu before, but didn't know why it was there. Should I try and use that instead?

---

### Post by nzadLithium on 2007-11-27
I'm pretty sure that 386 entry your saying is the 'safe mode'.

do gksudo gedit /etc/fstab

post the output here. The contents of that file are how its loading the various storage devices on your computer.

---

### Post by El Lance-O on 2007-11-27
No, it's not the recovery mode for the 2.6.22-14 kernel, it's actually the 386 architecture version, instead of the x86 version.

Here's the out put of fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e5fa576c-ab97-4b08-a124-105c154482fd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=74839b83-f4b6-4078-9fc9-5eb4267d1fed none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
UUID=38f81914-5093-4a6a-ba1a-36cde5065ae8  /boot ext3 defaults 0 0
```

---

### Post by nzadLithium on 2007-11-27
x86 means 386 486 etc. like when people  do *nix the mean anything to do with unix or linux or minux etc. i dont think you should be using one designed specifically for 386. I could be wrong though.

your fstab seems to be loading:
one ext3 partition (it looks like that is your main ubuntu one)
one swap partition
and one cd drive.

what partition do you have on sda2? is that your boot one?

it obviously isnt been told to mount your boot partition here and the error might be caused by the boot partition not being mounted so im thinking

goto the /boot directory in the file browser. If it doesnt exist or theres nothing in it or you get an error then do this in the terminal:
sudo mount /dev/sda2 /boot
(im hoping it will autodetect file system)
then go back and see if its there. If it is then post back and i'll try find a more permanent solution
if it brings up an error then post here what it says.

---

### Post by El Lance-O on 2007-11-27
Dell partitions include DellUtility which is some kind of recovery program, but it's windows so I don't understand why it's there. 

The other, OS, I do believe has some or symlinked files that are for boot.

And then the Filesystem which has /boot with all files there and intact. It just says that it isn't there in the GRUB boot.

---

### Post by stevesg1 on 2007-11-27
I hear you!! I ran 7.04 ok for ca 5 weeks. 

I found upgrade to 7.10 impossible by _any_ method on an unremarkable P4 Toshiba laptop, w/ winXP. After many failed/partial upgrades, even clean from 7.10 iso (which didn't like my 1024 x 768 svga monitor), I d/i a Gparted iso wiped every non-NtFS part, and re-installed 7.04. The 7.04 iso was d/l from Argonne and burned at 32X, then verified.

7.04 works fine enough for me. I even got a metapkg of the low latency kernel, jack, some apps, and did some midi composing.

I have no intention of upgrading to 7.10.

HEY ADMINS:

imho, the upgrade experience of many posters to these forums suggests that the ubuntu desktop world is powered by amateurs and adopted by fanboys. Convince me otherwise...

---

### Post by nzadLithium on 2007-11-28
this is getting really messy :S

goto your /boot folder and see if the new kernel you've installed is there. If it is then i can write up a line for you to add to your grub config file which will hopefully boot the kernel properly. This is install is really broken though so you are probably going to have more problems in the future.

I think it would be best if you just do a complete reinstall and by complete i mean you wipe any partitions dell have stuck on there and get your own ubuntu iso to reinstall it all these partitions are making it really confusing for me to know whats going wrong because you have so many partitions that i dont have a clue why they were made in the first place.

We can carry on trying to resolve this if you want but if the kernel isn't installed and the grub line that i give you doesnt work then I honestly don't have a clue how to fix. If it does work i am fairly sure you're going to keep having random problems like this in the future.

Anyway think about if this is really worth all the trouble its causing. I know reinstaling programs is a pain but when you copy out your home directory it should copy all your programs configs.

Post back whichever way you choose.
If you choose to carry on trying to fix this and the kernel you jsut tried to install is in that /boot folder then copy and paste the exact name here.

---

### Post by El Lance-O on 2007-11-28
Well, I think I may just go with doing a clean install.

But one more question: How would I back everything up?

I don't know much about partitioning, but I was told I could make a separate partition and move everything there, clear everything but that partition, move back, then delete that partition.

Would that work? If so, how would I get at doing this?

---

### Post by twist2b on 2007-11-28
you should have installed "KEEP" and set that up before you upgraded to an unstable version.........

edit -- keep is a program that lets you revert back to the last time you setup the thing.... to bad i wasnt smart enough to use it before i installed Java.... who knew it would eat my face!

---

### Post by nzadLithium on 2007-11-29
all you really need to keep is the home directory's. (if you back up anything else then you run the risk of pasteing the problem over the top again :D)I you cant fit them onto a disk of some description then i guess it is a viable option to stick it one a seperate partition but it seems a bit over kill to me. Heres how you would do anyway.

first run sudo apt-get install gparted

then run sudo gparted

pick a partition and resize enough space + another half gig (when it splits creates another file system it needs room for more file system info + a bit more space just in case) to stick all your home directories in.

restart ubuntu and hopefully the partition will show up. (if it doesnt then just say and ill give you a command to mount it) then just copy and paste the home folders onto it.

Reinstall ubuntu.

once its finished reboot then you could follow this thread: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

to get ubuntu to use your other home directory (the one you backed up)
or you could jsut copy and paste it over your new home directory.

---

### Post by DavidW2 on 2007-11-30
Reloading Ubuntu fresh should fix everything you are having issues with now but may introduce new problems.  That's because some settings that were necessary to make your hardware work with Linux may be lost.  I would think about investigating using SuperGrub to fix the Grub boot issues before reloading the whole thing.

See if you can boot the partition via SuperGrub's menu first and then go about fixing it from there.

Also, I had problems with my Nvidia driver after my Gutsy upgrade.  Can't remember off hand what I did to fix it but I'll investigate tomorrow and get back to you.

---

### Post by DavidW2 on 2007-12-01
To complete my post from the other day, I am not entirely sure what I did to get my graphics back.  I did have to run 'sudo dpkg-reconfigure xserver-xorg' a few times to get the right settings for things to running so I could see the screen. I believe I was still using the vesa or possible the nv driver at that time.  And I remember after that there was a restricted module update that allowed me to use the nvidia restricted module.  But I still cannot use any visual effects - so I guess I'm not the best person to talk about this but I to have my desktop back.

---

### Post by nzadLithium on 2007-12-02
I doubt he will come up with any hardware issues except having to install the latest video drivers.
That's unless he has some really weird hardware.

---

