---
title: "Feisty release: Failed to start the X Server"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by HKalnes on 2007-04-19
I have a Dell Inspiron 6400 laptop, with an ATI Mobility Radeon X1300. I have one Windows partition and one Linux partition on my disk, and need both because of my work. Until now I've been using Ubuntu 6.10, which worked OK after some hazzle with the ATI driver. The display's native resolution is 1680x1050.

I have prepared upgrading to Feisty, backed up files, and made a list of what I need to reinstall. I prefer to perform a clean install to avoid a "bloated" system.

Once Feisty was released earlier today I started by downloading the desktop-86 live/install CD. I checked it using Virtual PC, and found it OK and decided to go. I then booted from the CD. At first I made no selections in the boot menu. The boot process seemed OK until the point when I expected the desktop to show up. Then the screen went into text mode, and displayed the following error message:

**Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly.**

I then had the option to watch the log. I was for obvious reasons not able to save this to a file, so the following is from my hand written notes of what I thought might be interesting:

[FONT="Courier New"]
X-Window System Version 7.2.0
Release date 22 January 2007
X Protocol version 11, rev 0, release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Ubuntu hk3 2.6.20-15-generic #2 SMP
Sun Apr 15 07:36:31 UTC 2007 i686
Module Loader present
Backtrace: ........
Fatal Server Error: Caught Signal 11. Server aborting
[/FONT]

I was then asked whether I wanted so the detailed X Server output. I replied Yes, and got a very long list. The interesting part - I think - is at the end:

[FONT="Courier New"]
(II) VESA(0): Total memory 256 64KB banks
(II) VESA(0): Generic monitor: Using hsync value of 64.08 kHz
(II) VESA(0): Generic monitor: Using vrefresh value of 60.11 Hz
(II) VESA(0): Not using mode "1024x768" (no mode of this name)
(II) VESA(0): Not using mode "800x600" (no mode of this name)
(II) VESA(0): Not using mode "640x480" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(WW) VESA(0): No valid modes left. Trying less strict filter.
[/FONT]

And then followed by the same backtrace and error message (Caught signal 11) as above.

I then tried the safe graphics mode, and later also tried to select a resolution before booting the live CD. No success - same error.

So I thought that there might be something wrong with the live CD, and downloaded the alternate install in stead. So I went on and installed Feisty from that one, and everything seemed OK. No error messages during installed.

But when I booted it up, at the point where I expected to get the login, I got the same error message as above, with log and details.

So then what to do? I had a live CD for Feisty herd 4 lying around, and installed from that one in stead. After booting up, I ran [FONT="Courier New"]sudo apt-get dist-upgrade[/FONT] and it went on for about 30 minutes downloading and installing. So at that point, I should be update with today's release.

So I booted again - and the same error message as before appeared.

The error message suggests that I need to edit my configuration. That's where I'm stuck. I'm not very experienced with configuring in Linux/Gnome, all I've needed to do earlier has been to do some simple editing in the xorg.conf file. I also tried to edit the xorg.conf file, inserting my native resolution 1680x1050, but the result was exactly the same.

Does anybody have any tips? I'm grateful for any relevant feedback!

Helge
Oslo, Norway

---

### Post by kellemes on 2007-04-19
You better post your xorg.conf
Whatever the problem is, it will probably have to be fixed using this file..

By the way, you can always view your logfiles in /var/log/Xorg.0.log(.old)

---

### Post by nevertrustpeas on 2007-04-19
did you try using a lower resolution, such as 800x600? im nott 1oo% on this but your system may have set you monitor up incorrectly, so you may need to change both screen and monitor information to suit.

however my experience in linux is also very limited, :)

---

### Post by HKalnes on 2007-04-19
Yes, I tried booting the live CD with 800x600. Same error...

---

### Post by HKalnes on 2007-04-19
> **kellemes said:**
> You better post your xorg.conf
Whatever the problem is, it will probably have to be fixed using this file..

By the way, you can always view your logfiles in /var/log/Xorg.0.log(.old)

OK, I'll boot the 6.10 live CD again to get the xorg.conf in a little bit (I can't see the Linux drives from Windows, and the ext2/3 driver for Windows isn't yet Vista compatible).

---

### Post by HKalnes on 2007-04-19
> **kellemes said:**
> You better post your xorg.conf
Whatever the problem is, it will probably have to be fixed using this file..

By the way, you can always view your logfiles in /var/log/Xorg.0.log(.old)

Here's the  xorg.conf from my latest attempt:

[FONT="Fixedsys"]
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"no"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/wacom"	# Change to 
							# /dev/input/event
							# for USB
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
[/FONT]

---

### Post by lepascal on 2007-04-19
Hi,

I have exactly the same problem... I had it with the beta and I thought this would have been fixed in the final release...

---

### Post by HKalnes on 2007-04-19
Let's hope somebody knows how to fix it...

---

### Post by lepascal on 2007-04-19
I guess we could just install 6.10 and update it to 7.04 but I'd prefer a clean install.

---

### Post by rillip on 2007-04-19
I'm not extremely experienced, but I don't see anything in particular wrong with the xorg.conf.

However, if you want to try reconfiguring it without manually editing (might work, since you and I don't see anything particular sticking out), you can run the following:

sudo dpkg-reconfigure xserver-xorg

This will take you through a text-based config util, kind of like installing Windows 2k.  Pretty much, if you don't know a value, hit enter to get the most commonly used one.

---

### Post by kellemes on 2007-04-19
Probably an issue with the vesa-driver **but**... having an ATI-card, you want to use the open-source ati-driver or the official-fglrx driver.

There are a lot of guides on how to do this in the forums..

This is for installing fglrx-driver..
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

---

### Post by HKalnes on 2007-04-19
> **lepascal said:**
> I guess we could just install 6.10 and update it to 7.04 but I'd prefer a clean install.

I don't think that will work either. As I mentioned in my first post, I also tried starting with one of the alpha versions (that worked) and the upgraded it. Same problem...

---

### Post by HKalnes on 2007-04-19
> **kellemes said:**
> Probably an issue with the vesa-driver **but**... having an ATI-card, you want to use the open-source ati-driver or the official-fglrx driver.

There are a lot of guides on how to do this in the forums..

This is for installing fglrx-driver..
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

Thanx, but I'll need to get started with the vesa-driver first... I need to be able to log in graphically before installing the ATI-driver (which I also used earlier with 6.10).

---

### Post by HKalnes on 2007-04-19
> **rillip said:**
> I'm not extremely experienced, but I don't see anything in particular wrong with the xorg.conf.

However, if you want to try reconfiguring it without manually editing (might work, since you and I don't see anything particular sticking out), you can run the following:

sudo dpkg-reconfigure xserver-xorg

This will take you through a text-based config util, kind of like installing Windows 2k.  Pretty much, if you don't know a value, hit enter to get the most commonly used one.

Thanx,
Now I have tried that. There were some questions that I were a little bit in doubt about. I tried twice, the second time I disabled GLX. But both attempts were unsuccessful.

One question I was wondering about:
*Use Kernel framebuffer device interface?*
I left it at the default value "no" both times.
Is it worth trying again selecting "yes"?

---

### Post by arquetipo on 2007-04-19
I had no results trying to reconfigure xserver xorg and i think this is a major fault for ubuntu team. 
There are many many people buying new comps with ati graphic cards. If they can't simply install ubuntu, there is no possibility of being seduced by it...

Please, expert guys, fix this asap

---

### Post by lepascal on 2007-04-19
Maybe more people should have brought up this while 7.04 was still in alpha and beta stages... i didn't. We all learned something today. ;)

---

### Post by HKalnes on 2007-04-19
As mentioned, I used the alpha version herd 4 for a while, and did not have the problem. So this problem have been introduced during beta testing.

---

### Post by arquetipo on 2007-04-19
I think this is a new problem which came with this final release.
 I've read some posts saying it was possible to install alpha versions but not this one.

---

### Post by andbia on 2007-04-19
I tried the beta and it worked perfectly, but with the final i cant install anymore since X server fails to start. I have a Dell 6400 with ATI x1400.

---

### Post by trothigar on 2007-04-19
try 

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

worked for me

---

### Post by patrick1314 on 2007-04-19
I had the same problem with my X1400 card not 5 minutes ago.

What I did was follow the normal *[I]manual*[/I] install instructions on the ATI Linux Wiki: [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.36.5_Driver_Manually)

But instead of downloading the driver with firefox as I normally would, I used 'wget'.

```
wget -c https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.36.5-x86.x86_64.run
```

Apart from that, I followed the instructions exactly and it worked like a charm.

---

### Post by xlinuks on 2007-04-19
Or just don't ever buy ATI video cards, I had problems with them not only on Linux as such, but on windows too! For me the word "ATI" means "random troubles".
If you respect yourself and your time buy next time a nVidia card. Since the day I dropped ATI I never looked back!

---

### Post by mcgooie on 2007-04-19
Im having lots of probs too, tried reconfigure and no luck will try the alternate cd and the install method patrick mentioned

---

### Post by Ubertakter on 2007-04-19
I was having a similar problem with Xserver, except that I have a Nvidia 7600GS.

Here is what I went through:
I went to [http://ubuntuforums.org/showthread.php?t=187177]("http://ubuntuforums.org/showthread.php?t=187177")
and followed the instructions there.

I skipped the first command since this was a fresh install and ran the second:
```
dpkg-reconfigure xserver-xorg
```

This asks for a lot of specific information about your video card and monitor.  I happen to have all of that handy.  When in doubt I just used the defaults.

I then ran the next command:
```
dpkg-reconfigure gdm 
```
since I'm going to run gnome.  This restarted gnome and I'm now in the window manager like I should have been in the first place.  I'm going to attempt an install now.  I'll let you know how that goes.

---

### Post by muchmusic on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=413890](http://ubuntuforums.org/showthread.php?t=413890) is from the intel mac forum area and refers to the relevant bug, [https://bugs.launchpad.net/bugs/89853](https://bugs.launchpad.net/bugs/89853)

I'm trying the alternate CD, then the method of installing fglrx from the commandline

---

### Post by KennyG3987 on 2007-04-19
[http://ubuntuforums.org/showthread.php?t=413997](http://ubuntuforums.org/showthread.php?t=413997)

try this worked for me

---

### Post by carpex on 2007-04-19
If you want to do that from the live CD (installing fglrx), I guess you need to be connected to a network through DHCP, right? I tried configuring my network connection manually with etc/network/interfaces and /etc/resolv.conf, but I couldn't get a network connection working (I'm on a static IP). Any other steps I need to follow? Sorry if this is not directly related to this thread. 

GL

---

### Post by arquetipo on 2007-04-19
I've just downloaded the file needed to complete the installation but using another computer:
[http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb)

Is it possible to use that file to fix xorg at the installation? That would solve my problems because i don't have internet on my laptop.

---

### Post by HKalnes on 2007-04-19
Problem is now solved for me:
- Reinstalled from scratch with the alternate CD
- Rebooted and did a command line login after the error occurred
- Installed the fglrx drivers using the [Instructions for 6.10 (Edgy)]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") .

:) Thanx for all replies - hopefully others will find this thread helpful!

I have to agree that the ATI-drivers suck, actually when running Vista I use the drivers from Microsoft rather than the ones from ATI. There will definitely not be an ATI card in my next computer!

---

### Post by muchmusic on 2007-04-19
Agreed on using the ati drivers... it did work though!

---

### Post by laughingLoki on 2007-04-19
> **HKalnes said:**
> Problem is now solved for me:
- Reinstalled from scratch with the alternate CD
- Rebooted and did a command line login after the error occurred
- Installed the fglrx drivers using the [Instructions for 6.10 (Edgy)]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") .

:) Thanx for all replies - hopefully others will find this thread helpful!

I have to agree that the ATI-drivers suck, actually when running Vista I use the drivers from Microsoft rather than the ones from ATI. There will definitely not be an ATI card in my next computer!

I'm having the same problem that you described, except I have a Dell Latitude D600 with an ATI Mobility Radeon 9000 card.  I upgraded instead of installing 7.04 from scratch.

I'll try the solutions posted here, and I'll make sure to reply with whichever one works for me.

I wish I had an NVIDIA card.  *sigh*

---

### Post by bignickel on 2007-04-19
> This is for installing fglrx-driver..
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

I have a Dell Inspiron 8600 with an ATI card, and Feisty looked terrible on it, and not much better when I used the "Restricted Drivers Manager" to install the driver.

I just followed the instructions in the wiki above and now everything looks great.

---

### Post by arquetipo on 2007-04-19
sorry, but i'm not getting the point. 
Do I need an internet connection to take that file? 
If not where can i find it? Seems it isn't in the repositories of the live cd...

Thanks

---

### Post by trothigar on 2007-04-19
yep fraid so.

---

### Post by arquetipo on 2007-04-19
> **trothigar said:**
> yep fraid so.

can I point out a location on my hard disk?
I'll try to download the critical file from the other comp and then paste it into my laptop

---

### Post by TheTuna on 2007-04-19
I'll be installing this evening on my box.  I've got an ATI Radeon X1300 Pro.  I'm glad I read this thread first.

Note: I agree that the ATI Drivers have been a pain, but I still prefer their hardware over nVidea.  Not just because I have an ATI... I've had both, and I was more impressed with the ATI's I've owned.  

Just my .02

---

### Post by odelay on 2007-04-19
So does this mean each time I want to use the Feisty LiveCD in the next 6 MONTHS I'm going to have to manually install the fglrx driver?!?  How did a problem affecting practically everyone with a recent ATI card (and was working fine in Beta releases) make it into the *final* Feisty release?

I don't mean to sound overly critical or unappreciative, but it is a little puzzling.  Just imagine what first-time Linux users are thinking...

---

### Post by laughingLoki on 2007-04-19
I wasn't able to get the driver working with my card.  I don't think the old driver is compatible with Xorg 7, and the new ATI driver doesn't work with my card.

I just restored my xorg.conf.orginal-0 file; now I'm using the open source drivers.

It's not like the ATI drivers were that good, anyway.

---

### Post by carpex on 2007-04-19
I guess they are working on it:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/89853)

This seems to be a problem upstream. Hope it is fixed soon.

GL

---

### Post by odelay on 2007-04-19
Links broken.

I don't suppose they'd be able to coordinate releasing a LiveCD with the fix...I imagine once it's released, it's released.  This is going to be a pain for people (like me) who plan on doing a fresh install.

---

### Post by arquetipo on 2007-04-19
> **odelay said:**
> So does this mean each time I want to use the Feisty LiveCD in the next 6 MONTHS I'm going to have to manually install the fglrx driver?!?  How did a problem affecting practically everyone with a recent ATI card (and was working fine in Beta releases) make it into the *final* Feisty release?

I don't mean to sound overly critical or unappreciative, but it is a little puzzling.  Just imagine what first-time Linux users are thinking...

if you don't have internet you simply can't intall manually.
The critical file isn't inside the repository folder of the live cd.
what i am trying to do now is to burn an image of ubuntu and after add the ******* file....

A newb like me loose hours trying to fix the problem. Besides it, the majority of linux rooks doesn't spend that time trying over and over.
I think problems like this are the worst enemy of linux.

---

### Post by muchmusic on 2007-04-19
[https://bugs.launchpad.net/bugs/89853](https://bugs.launchpad.net/bugs/89853) should work properly as a link to the bug.

---

### Post by ned99 on 2007-04-19
Hi, I've got the same problem with the X1600 card on my laptop. BUT I can't use the ATI drivers as they cause my comp to shutdown after about 5 minutes. Is there a way to fix this bug without using the fglrx drivers? 

Thanks.

---

### Post by odelay on 2007-04-19
Hey **ned99**,

I haven't tried this yet, but it's working for some people.  It was originally posted on the bugfix page (see **muchmusic's** post directly above).

> The solution is editing xorg.conf and adding "HorizSync	36-52" and "VertRefresh	36-60" in "Section Monitor". Giving a startx, the desktop appears with normal resolution for the vesa driver (cannot use radeon driver on this machine).
Also, a sudo dpkg-reconfigure xserver-xorg, even accepting all default choices, solves the problem.

---

### Post by ptzink on 2007-04-19
Okay, I have somewhat of a stupid (newb) question. I did a fresh install of 7.o4 Herd 4 a few months back (because I could not get 6.10 to work on my new system). It has been running fine and I have been installing updates on a regular basis. My question is do I need to 'upgrade' to the official 7.04 release or am I already updated because I have been running Herd 4 from the get go? All you 'Herders' please advise.
Thanks in advance...

---

### Post by arquetipo on 2007-04-20
I had to make a boot cd for my own in order to get feisty installing without internet connection.
I'll let him on the share folder of my e-mule and you can search there for: Ubuntu.Desktop.7.0.4-Desktop-[ATI_included].iso

When you enter the console after the error, instead of typing "sudo apt-get install xorg-driver-fglrx" do the following:

sudo dpkg --install /pool/restricted/l/linux-restricted-modules-2.6.20/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

I hope this will work for all!

---

### Post by pointone on 2007-04-20
Same problem here, but dpkg-reconfigure xserver-xorg and editing HorizSync and VertRefresh did not work for me. Instead, I ran:

```
sudo X -configure
sudo cp /home/ubuntu/xorg.conf.new /etc/X11/xorg.conf
startx
```

... after the installer dumped me to the console. This allowed me to start X fine and install.

---

### Post by mcgooie on 2007-04-20
> **arquetipo said:**
> I had to make a boot cd for my own in order to get feisty installing without internet connection.
I'll let him on the share folder of my e-mule and you can search there for: Ubuntu.Desktop.7.0.4-Desktop-[ATI_included].iso

When you enter the console after the error, instead of typing "sudo apt-get install xorg-driver-fglrx" do the following:

sudo dpkg --install /pool/restricted/l/linux-restricted-modules-2.6.20/xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

I hope this will work for all!

I have tried all the mentioned ways and its still not working for me. Can you tell me if the iso you created will boot as i tried to make my own and i get a "checksum error"?

---

### Post by arquetipo on 2007-04-21
> **mcgooie said:**
> I have tried all the mentioned ways and its still not working for me. Can you tell me if the iso you created will boot as i tried to make my own and i get a "checksum error"?

It worked fine for me...
If you want to make one by your own you have to b carefull by using the appropriate programs to open the original iso and to compile the new one. 
Another important issue related with that is to export boot information from the original and to apply that to the built one. The last thing you should do is to delete something not important in order to get enough space for the driver in the range of 700Mb.

Anyway you can download the iso from e-donkey server:
ed2k://|file|Ubuntu_7.04_FeistyFawn_Desktop_[ATI_fixed].iso|731758592|A86B0CF3EFDF603BC1698A14A0FC2257|h=MJ6CEPDXFUK4GQDG6BRTYVC3AOQCKGUV|/ 
Good luck

---

### Post by smlsteve on 2007-04-22
same exact error as all of you
Dell XPS M2010,ATIx1800,240  gig non RAID dual boot Feisty/Vista

---

### Post by IngmarBlonk on 2007-04-23
You don't need that special iso, just take that *.deb file and burn it on a blank cd or put it on a usb-stick.
Put that cd/usb-stick in your pc, mount it and do 'dpkg -i /path/to/the/file'.
That will install the file now just run the other commands.

---

### Post by ph0neman on 2007-05-02
just an -=fyi=- i did the upgrade from 6.10 and had the same problem as the clean install...

---

### Post by nashjc on 2007-05-03
I've an ACER Aspire 5050 (-5554 are the add-on numbers, but they seem to be a daily change).

I got the dreaded "Failed to start X server".

Trothigar's suggestions worked for me. THANKS! After X came up I got a msg that I was using restricted drivers and to learn more ..., but when I clicked the icon, I was told I wasn't root (surprise! gdm usually set to prevent root login). 

Anyway, I don't see too many posts suggesting that they went through all the steps he proposed, though there are some that refer to getting restricted driver 'debs', and then folk have wandered off into CD image issues. 

It would likely be helpful to the Ubuntu folk to know how many people get the X server problem and also if something along the lines Trothigar suggested solve it, so they can put this in the upgrade.

JN

---

### Post by faithsnathan on 2007-05-03
> **nashjc said:**
> 
It would likely be helpful to the Ubuntu folk to know how many people get the X server problem and also if something along the lines Trothigar suggested solve it, so they can put this in the upgrade.

JN

If anyone is interested in how many, I know I've experienced this.  It took me forever and a lot of hair pulling to figure out how to back it back up to Edgy.  So I'll stay with Edgy for a while until I know this has been fixed.  :(

---

### Post by trashjedi on 2007-05-04
I also have the problem of the Xserver problem with the live CD, and for installation with the same Dell configuration, which means that because I'm not experienced, and have exams, I didn't want to try installing it and not being able to use my linux, and therefore spending hours on trying to fix it, which shouldn't be the case.
I'll try the script as soon as my exams finish! Thanks for all the people like empowered who help newbies like me enjoy linux a bit more. 
I hope I'll learn how to do it myself in the future.:)

---

### Post by Ub1476 on 2007-05-12
This worked perfect for me:

1) Boot from cd
2)Choose start/install ubuntu
3)When the error message comes, choose "No" to all questions, and you'll come to the terminal.
4) Follow the code:

```

sudo apt-get update

sudo X  -configure
sudo cp /home/ubuntu/xorg.conf.new /etc/X11/xorg.conf

sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

```

Remember to have internet connection! I recomend NOT to use wireless, cause it's probably not set up correctly when you haven't installed Ubuntu yet:p

After you have installed, the computer will restart and you probably will have to install the fglrx drivers again. After that everything should be fine.

---

