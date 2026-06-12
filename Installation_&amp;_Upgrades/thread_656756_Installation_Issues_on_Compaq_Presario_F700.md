---
title: "Installation Issues on Compaq Presario F700"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by Atlai on 2008-01-02
I just recently became a fan of linux when I installed it on my old Dell laptop a few months ago. Yesterday I bought a Compaq Presario F700 with the following system specs:
AMD Turion 64x2 1.9 Ghz
nVidia GeForce 7000m
Atheros AR5007 WiFi card

I need to do a dual boot system, and I already split my hard drive into 70 GB for Vista and 70 GB of unpartitioned space for Ubuntu. My first issue arose when the install CD booted all the way to GNOME. A single window popped up and said that it was running in Low Display Quality Mode.I searched for any drivers that were close to my hardware, but could find nothing so I hit "Continue" and GNOME went away. The screen said something about loading libraries, but never did anything after that. After approximately 30 minutes, I shut off the computer and tried again with no luck. 

I searched in here and saw that some people had similar problems. I then booted the install cd with the "noapci pnpbios=off" option after seeing that advice in a thread. Same thing happened. After doing another search, I realized that lots of people are having problems with 7.10 on HP/Compaq computers. Would 7.04 work better? I was really starting to enjoy linux and going to Vista now sucks.

---

### Post by Ex-windows on 2008-01-03
I have a similar Laptop
How did you get it to install? I cant get passed the xserver.
I posted Here
[http://ubuntuforums.org/showthread.php?t=656797](http://ubuntuforums.org/showthread.php?t=656797)
But nothing yet.
Anynhelp/advice would be greatly appreciated

---

### Post by h4mx0r on 2008-01-04
load up the livecd and use option 2.... yes just press down then enter. restricted drivers manager will take care of direct rendering for the nvidia card too once the system is installed.

---

### Post by Ex-windows on 2008-01-05
A belated Thank you for the info. And you are right. I accidentily hit the Safe graphics mode option and imagine my surprise lol. This after downloading and burning Fiesty alternete cd and Gutsy (both versions). I haven;t installed yet but it sure was fantastic using ubuntu on  a new er faster machine. even using the live cd was faster than my desktop. Anyway I really do appreciate the input  Thanks and Take care

---

### Post by slarrabe on 2008-01-10
> **h4mx0r said:**
> load up the livecd and use option 2.... yes just press down then enter. restricted drivers manager will take care of direct rendering for the nvidia card too once the system is installed.

I had a similar problem with my Compaq (same system specs as the original poster) and was able to install it as you described.  Unfortunately, I'm stuck with 800 X 600 resolution and can't install the nvidia drivers.  When I try to enable the drivers I get an error saying the nvidia-glx-new package is not enabled.  I Googled this and went to the Ubuntu website which said to run "sudo nvidia-glx-config enable."  Trying this, the terminal tells me to try "sudo apt-get install <selected package>."  Upon doing this, I get the following errors:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I also tried logging in as root but the main login screen wouldn't let me. :(  If there is any way I can get these drivers enabled so I can access higher resolutions (and, hence, see the buttons at the bottom of the windows :mad:) I'd be eternally grateful.

---

### Post by anoopjohn on 2008-01-11
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/13856](https://answers.launchpad.net/ubuntu/+question/13856) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I think there is a problem with nVidia m7000 chipset. I had once searched for it and if i remember correctly you can work around by downloading the latest binaries from the nvidia site. Do check out this option.
Here is a link from launchpad related to this.
[https://answers.launchpad.net/ubuntu/+question/13856](https://answers.launchpad.net/ubuntu/+question/13856)

---

### Post by slarrabe on 2008-01-11
I downloaded the drivers but can't install them :mad:.  Apparently, I can only install them as root.  Unfortunately, I can't seem to login as root at all.

---

### Post by anoopjohn on 2008-01-11
you dont have to login as root. Just use sudo command to run command as root.

---

### Post by Pumalite on 2008-01-11
[http://ubuntuforums.org/showthread.php?t=643195](http://ubuntuforums.org/showthread.php?t=643195)
alternate installation CD of Gutsy Gibbon 7.10 with the nodma parameter. It also refuse to read the hdb - a protected partition installed by the Compaq rescue CD used to back up files/system. I think the nodma parameter might have had something to do with fixing that.

---

### Post by mousingsurface on 2008-01-13
I got the Nvidia driver going.  However, I do not have the Wifi working.  Does anyone have instructions on how to get that working?

Thanks

---

### Post by anoopjohn on 2008-01-14
Did you try to enable the restricted firmware?

---

### Post by wtfacoconut on 2008-01-16
yo man, I got the same laptop with the exact same problems. I was wventually able to get around my wireless networking problem by downloading and installing NDISwrapper. I Highly suggest that you just go and compile it from source instead of using the one provided Synaptic package manager cause I was told that for some reason the .deb packages have got some sort of bug where it will screw up the kernal. you will need the build-essentials package to be installed (good news is that it's on the ubuntu live cd and all you have to do is put the cd in and install build-essentials package through Synaptic.) Assuming that you already downloaded the wireless drivers, copy the *.inf file to where ever u want, Pop open a terminal and cd into the directory where the *.inf file is at then type 
```
 ndiswrapper -i *.inf 
```
then 
```
 ndiswrapper -mi 
``` 
hopefully all went well. All you gotta do is reboot and hopefully modprobe picks up the wifi card. It worked for me but if ya'll got issues try using a using a USB WiFi card. The ndiswrapper homepage has a list of supported cards along with the tips needed to get them working. I'm still working on trying to get the Nvidia drivers working but those are proving to be a real pain in the ***. Any help on that topic will be greatly appreciated. :guitar: :popcorn:

---

### Post by wtfacoconut on 2008-01-16
okok since I'm a complete noob at this gay nvidia drivers thing I'm feeling pretty accomplished after tinkering with my xorg.conf file and other stuff. But I was finally able to get it running and I was able to fix that stupid 800x600 resolution thing and pump it up to 1024x768. Assuming that there are people out there with this notebook ( and also that you installed version:169.07) and still trying to get this damn thing to work here's a copy of my xorg.conf file:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:09:35 PST 2007

# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
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
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:0:18:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768"
	EndSubSection
EndSection

```

Now...Here's the thing. I havn't been able to get the 3D support thing up and running yet. I think that I have the right version of "linux-restricted-modules installed" to match match the version of the running kernel. Anyone know how I will be able to fix that??? I really want to run compiz/beryl. (^_^):KS:popcorn:

---

### Post by slarrabe on 2008-01-17
Finally got the drivers to work!  Turns out I had the drivers in the wrong directory.  I put them on the desktop instead of the home directory (I'm such an n00b).  Now screen resolution is up to 1280 x 800, just the way I like it.:popcorn:

---

### Post by timsath on 2008-01-20
I have a Presario F700 series, the model is actually F756NR, it has a built in Atheros card, but I couldn't get madwifi to read the card...I ended up just downloading the windows XP 32-bit drivers off of the atheros site and using ndiswrapper.  To my surprise everything worked great!  WPA2 encryption and all that.  The only hurdle I'm facing is the inability to mute the external laptop speakers, I can either have sound through the headphones and the speakers, or no sound at all.  Has anyone else solved this issue?  Thanks!

---

### Post by slarrabe on 2008-01-22
Grr.  Got another problem as a result of installing the drivers.  My window borders no longer appear around my windows.  This means I can't minimize/maximize or close windows using the three buttons on the border.  It's also frustrating trying to determine where one window ends and another begins.  Here's a screenshot.

[http://s258.photobucket.com/albums/hh260/slarrabe/?action=view&current=windowprob.png](http://s258.photobucket.com/albums/hh260/slarrabe/?action=view&current=windowprob.png)

---

### Post by wtfacoconut on 2008-01-25
Crap!!! Well... It seem that every time I shutdown/reboot the kernel module for my nvidia driver gets erased. any of ya'll got a solution to that??? also I got the same problem with my sound. It seems that when I plug in my headphones the speakers on my computer keep playing as well. Help and love would be greatly appreciated.

---

### Post by slarrabe on 2008-01-25
Yeah I've got the sound issue as well.  It doesn't bother me all that much considering the other problems I have.  The best way I've found to get around this is play with the volume settings on my computer and headphones so I can't hear anything from the speakers but can from the headphones.

---

### Post by Pumalite on 2008-01-25
You guys should try:
sudo apt-get install linux-backports-modules-generic
Reboot and see if your sound and wifi cards are recognized.

---

### Post by slarrabe on 2008-01-25
I would do just that if I could get the terminal to work properly.  All I get is a white screen.  This, and the disappearance of my window borders (see one of my previous posts) occurred after I installed th nVIDIA drivers.

---

### Post by wtfacoconut on 2008-01-27
> **slarrabe said:**
> Yeah I've got the sound issue as well.  It doesn't bother me all that much considering the other problems I have.  The best way I've found to get around this is play with the volume settings on my computer and headphones so I can't hear anything from the speakers but can from the headphones.

call me stupid buuuut.....
which program in gnome did you use to tweak the volume settings between your headphones and speakers. All of the setting managers that I've messed with arn't showing me a headphone setting....Maybe I don't got the right sound card drivers...
And....
> **Pumalite said:**
>  You guys should try:
sudo apt-get install linux-backports-modules-generic
Reboot and see if your sound and wifi cards are recognized.
I tried your step as well...sry man it didn't work..Is there a similar program like ndiswrapper where it will let me use use windows drivers for the sound card in linux...I don't think there is but it's worth akin' anyways.

---

### Post by Greg T. on 2008-01-27
In case you weren't aware, there's a thread on a similar version of the Compaq Presario F700, the F730US:

[http://ubuntuforums.org/showthread.php?t=643195](http://ubuntuforums.org/showthread.php?t=643195)

---

### Post by slarrabe on 2008-01-28
> **wtfacoconut said:**
> call me stupid buuuut.....
which program in gnome did you use to tweak the volume settings between your headphones and speakers. All of the setting managers that I've messed with arn't showing me a headphone setting....Maybe I don't got the right sound card drivers...
And....

I tried your step as well...sry man it didn't work..Is there a similar program like ndiswrapper where it will let me use use windows drivers for the sound card in linux...I don't think there is but it's worth akin' anyways.

To tinker with the volume control settings, I selected (oddly enough) Volume Control from Settings -> Preferences.  If it doesn't show up you will have to edit your menus.  To do this, right click on the menu bar and select Edit Menus.  On the left list, select Preferences.  On the right scroll down and check Volume Control.  Click Close.  Volume Control should now be available in Preferences.

In Volume Control I reduced the volume considerably until it could not be heard from the speakers.  Then, I cranked up the volume on my headphones via the volume control on them.  Hope this helps.

As for Pumalite's suggestion, I managed to try it but it didn't work either.

---

### Post by Pumalite on 2008-01-28
Check 'uname -a'. Make sure you have 22.14-generic

---

### Post by wtfacoconut on 2008-01-31
Yup...I'm using that kernel. I'm just about of Ideas. I'm just gonna try and install a mess load of drivers and other packages in synaptic and see what happens. Also I tried that whole sound control thing and it didn't work. As a matter of fact I didn't even see a setting for my headphones, all i saw was Master, PCM, and Digital.

---

### Post by wtfacoconut on 2008-02-01
> **Greg T. said:**
> In case you weren't aware, there's a thread on a similar version of the Compaq Presario F700, the F730US:

[http://ubuntuforums.org/showthread.php?t=643195](http://ubuntuforums.org/showthread.php?t=643195)

Ya I took a look at that thread and it did help me with one thing, but there are a few hardware differences that it doesn't address and/or doesn't apply to this one (which really really sucks). But thanks any dude. Oh I'm also working on a script to auto reinstall the Kernel modules at boot, so just incase anyone else has this problem also I'll post it for your viewing pleasure.

But the sound it the one thing that is really p;ssing me off. The speakers don't want to turn off when I plug in the headphones. Maybe ALSA is the wrong thing to be using or the drivers arn't right. Any thoughts??? I got cookies!!!!!!!  XD

---

### Post by tewest99 on 2008-02-20
Are you able to get 1280 x 800 screen resolution after getting the Xserver working with NVidia card?

---

