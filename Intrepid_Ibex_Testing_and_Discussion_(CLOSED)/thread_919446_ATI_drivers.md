---
title: "ATI drivers"
date: 2008-09-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2008-09-14
I just upgraded to Ibex. I was having some major problems getting fglrx working and at my monitor's correct res. The upgrade seems to have made the res work properly. 

I'm wondering how I can enable a video driver, as fglrxinfo gives me this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.1)

The xorg.conf is set to defaults, no driver specified. I am not seeing the fglrx driver in the restricted driver box either, though it's still installed.

---

### Post by inportb on 2008-09-14
fglrx does not work with the current version of Xorg, though AMD's Linux dude said that they're working on it.

If you use a blank/default xorg.conf, the opensource radeon driver would be used. For most purposes, this driver works just fine and supports 2D+3D acceleration. You should remove fglrx for now, to avoid conflict with the radeon driver; it doesn't work anyway.

If you'd like to mix Compiz and video playback, you'd need to enable EXA, according to MALEADt. It works.

---

### Post by lewmnik on 2008-09-14
> **inportb said:**
> fglrx does not work with the current version of Xorg, though AMD's Linux dude said that they're working on it.

If you use a blank/default xorg.conf, the opensource radeon driver would be used. For most purposes, this driver works just fine and supports 2D+3D acceleration. You should remove fglrx for now, to avoid conflict with the radeon driver; it doesn't work anyway.

If you'd like to mix Compiz and video playback, you'd need to enable EXA, according to MALEADt. It works.

Radeon does not work on amd64... Here's hoping the linux dude is right :confused:

---

### Post by Enigmatic on 2008-09-14
I should be able to enable desktop effects with the default driver then, no? I'm not able to do that, which makes me wonder what I have installed. Is there any way to check for sure if it's running the Radeon driver? I'm also noticing scrolling, switching between windows and sometimes window drawing is a bit sluggish (might be related).

I'm not convinced that 3D is working correctly due to running glxgears that gave me about 400fps. I thought it would normally give thousands for a highend card if 3D was working?

---

### Post by Enigmatic on 2008-09-16
Can somehow tell me how I can "enable" (?) the correct driver on my desktop? My laptop is quite zippy, but my desktop is slow at switching windows, scrolling and rendering pages etc. It seems to be a graphics problem, as the fps in glxgears is so much slower than the laptop despite having a far better card. Both appear to have the "radeon" driver specified in xorg, and both CANNOT enable desktop effects.

What I'm seeing:

**Laptop**: X700
fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.1

glxgears: 1025fps

xorg.conf: [http://pastebin.ca/1204371](http://pastebin.ca/1204371)

**Desktop**: HD4850

fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 1.4 (2.1 Mesa 7.1)

glxgears: 600fps

xorg.conf: [http://pastebin.ca/1204370](http://pastebin.ca/1204370)

---

### Post by bpl07 on 2008-09-16
You need to completely remove every package having to do with fglrx, then reinstall the radeon driver.  There is a conflicting libGL.so object file between the 2 drivers.

Once done, simply put 'Driver "ati"' in the device section of xorg.conf.  There are other settings for dri and such, let us know when you get this far though.

---

### Post by Enigmatic on 2008-09-16
ok, I will remove anything with fglrx in it (purge) and then reinstall the xserver-xorg-video-radeon pkg?

---

### Post by thonuz on 2008-09-16
I have a Toshiba m305D with ATI Radeon 3100 graphics. I just installed Alpha 5 fine, but after recent updates (xorg included) I get a blank white desktop. I can log out and in and see that screen fine though. My xorg.conf file has nothing in it about drivers. Is there an  ATI driver I need to apt-get? I've also tried adding "ati" or "radeon" to xorg.conf driver section.

---

### Post by bpl07 on 2008-09-16
> **Enigmatic said:**
> ok, I will remove anything with fglrx in it (purge) and then reinstall the xserver-xorg-video-radeon pkg?

Yes, or the xserver-xorg-video-ati, which depends on the radeon one.

---

### Post by olskar on 2008-09-16
May I ask how the performance is with the opensource driver in Intrepid? That depends on the card of course, I have a x600..

And speaking of aticards, I don't understand the series they use..apparently my x600 is part of some kind of r-series? Which one?

---

### Post by t.alex on 2008-09-16
> **Enigmatic said:**
> ok, I will remove anything with fglrx in it (purge) and then reinstall the xserver-xorg-video-radeon pkg?

if you want to reinstall your libGL.so library, you'll have to reinstall *libgl1-mesa-glx*
```
$ dpkg -L libgl1-mesa-glx|grep libGL
/usr/lib/libGL.so.1.2
/usr/lib/libGL.so.1
```

---

### Post by bpl07 on 2008-09-16
> **olskar said:**
> May I ask how the performance is with the opensource driver in Intrepid? That depends on the card of course, I have a x600..

And speaking of aticards, I don't understand the series they use..apparently my x600 is part of some kind of r-series? Which one?

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Yours is the r300 series.

---

### Post by excogitation on 2008-09-16
> **olskar said:**
> May I ask how the performance is with the opensource driver in Intrepid? That depends on the card of course, I have a x600..

Performance is acceptable (could always be better, not?).

X700 mobility:
```
glxgears 
7000 frames in 5.0 seconds = 1399.033 FPS
5783 frames in 5.0 seconds = 1156.504 FPS
6145 frames in 5.0 seconds = 1228.674 FPS
9329 frames in 5.0 seconds = 1865.704 FPS
8710 frames in 5.0 seconds = 1741.945 FPS

```

---

### Post by Enigmatic on 2008-09-16
Maybe I did something wrong, but I still can't get it to work.

I purged anything with fglrx in the title.
Rebooted.
Purged xserver-xorg-ati/radeon/radeonhd. Then installed them again.
Rebooted.
Reinstalled the libg1-mesa-glx pkg.

I'm still seeing 300fps in glxgears! Compiz also doesn't work, so apparently 3D isn't properly working. Not sure if I have to do anything different for a HD4850 given it's recent introduction?

Relevant part of xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
        Option          "AccelDFS"      "off"
        Option          "AGPMode"       "1"
        Option          "AGPFastWrite"  "1"
EndSection

---

### Post by MALEADt on 2008-09-16
> **Enigmatic said:**
> Maybe I did something wrong, but I still can't get it to work.

I purged anything with fglrx in the title.
Rebooted.
Purged xserver-xorg-ati/radeon/radeonhd. Then installed them again.
Rebooted.
Reinstalled the libg1-mesa-glx pkg.

I'm still seeing 300fps in glxgears! Compiz also doesn't work, so apparently 3D isn't properly working. Not sure if I have to do anything different for a HD4850 given it's recent introduction?

Relevant part of xorg.conf:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
        Option          "AccelDFS"      "off"
        Option          "AGPMode"       "1"
        Option          "AGPFastWrite"  "1"
EndSection

You got a HD4850, which communicates as far as I know almost certainly through the PCI-E bus... Then why are you enabling AGP options?

This should be better:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
EndSection
```

Or if you want to make those tweaks PCI-E compatible:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
        Option          "AccelDFS"      "1"
EndSection
```
Wiki's entry on AccelDFS: *1/0 On for PCIE, off for AGP* :)


BTW
```
tim@tim-desktop:~$ glxgears
13962 frames in 5.0 seconds = 2792.267 FPS
14211 frames in 5.0 seconds = 2842.118 FPS
14157 frames in 5.0 seconds = 2831.248 FPS
14219 frames in 5.0 seconds = 2843.758 FPS
14217 frames in 5.0 seconds = 2843.290 FPS
```
Performance is quite acceptable on this Sapphire X1650 Pro (R520).

---

### Post by Enigmatic on 2008-09-16
Here is my xorg.conf. I'm still getting 300fps.

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
        Option          "AccelMethod"   "EXA"
        Option          "AccelDFS"      "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by niglet101 on 2008-09-16
try this

[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by t.alex on 2008-09-16
> **Enigmatic said:**
> Not sure if I have to do anything different for a **HD4850** given it's recent introduction?


Open source 3D drivers are not (yet) available for your card! You'll have to stick for another couple of months with fglrx.

---

### Post by Enigmatic on 2008-09-16
Yay...but isn't an 8.10 compatible fglrx going to be released in time for 8.10's release?

---

### Post by t.alex on 2008-09-16
Catalyst 8.9 should appear this days. Perhaps you (and many other) get lucky and it will work with the new X-Server :)

---

### Post by soxs on 2008-09-16
> **t.alex said:**
> Catalyst 8.9 should appear this days. Perhaps you (and many other) get lucky and it will work with the new X-Server :)

Yes it will, but nobody can say wether it supports the new kernel nor the new xserver/xorg/mesa release.

btw. RadeonHD 4870 gives me 5007.754 fps though that doesn't indicate anything.

---

### Post by Enigmatic on 2008-09-16
> **soxs said:**
> Yes it will, but nobody can say wether it supports the new kernel nor the new xserver/xorg/mesa release.

btw. RadeonHD 4870 gives me 5007.754 fps though that doesn't indicate anything.

Strange indeed, does 3D work for you? I am still not able to use compiz.

---

### Post by Enigmatic on 2008-09-16
To be honest, I really don't care so much about 3D, but I use FTPRush via Wine a lot, and have noticed that the time it takes to render a directory on screen when you go to it takes several seconds, instead of being nearly instant like it's always been. I've just been assuming that this might be a graphics problem, but if there's some other way of solving it I would be very happy to hear it!

My laptop appears to be using the radeon driver and does not have this problem, however it is running the X700 instead of HD4850, so maybe the support that's there for the X700 has something to do with it.

---

### Post by RAOF on 2008-09-16
> **Enigmatic said:**
> ...
My laptop appears to be using the radeon driver and does not have this problem, however it is running the X700 instead of HD4850, so maybe the support that's there for the X700 has something to do with it.

There's currently no acceleration at all - not 2d, not 3d - for r7xx cards (of which the HD4850 is one).  This is likely why your app is drawing slow :)

---

### Post by Enigmatic on 2008-09-16
Wonderful :) What sort of timeframe is it going to take for a driver to be released?

---

### Post by BwackNinja on 2008-09-16
[http://www.phoronix.com/scan.php?page=article&item=amd_rv730_oss&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_rv730_oss&num=1)

that about sums up whats happening with it

---

### Post by Enigmatic on 2008-09-16
Well a 2 week wait at most shouldn't be too bad.

---

### Post by soxs on 2008-09-17
> **Enigmatic said:**
> Strange indeed, does 3D work for you? I am still not able to use compiz.

Yes it works just fine for me. I can etqw/savage2/nexuiz/warsow/urbanterror/sauerbraten all @ ultimate settings

Edit: 
I allready posted multiple times how I install fglrx everytime:
```
sudo apt-get remove --purge fglrx-amdcccle* xorg-driver-fglrx*
```
(postback if you encounter any errors! Don't go on!)
and then follow:
[http://ubuntuforums.org/showpost.php?p=5711572&postcount=4](http://ubuntuforums.org/showpost.php?p=5711572&postcount=4)

---

### Post by isrich on 2008-10-04
Hi
Is it possible to make HD4670 work with intrepid??

It work well on hardy with catalyst 8.9 but not in intrepid.

I know that ATI Driver did not support xorg 7.4 now but is there any solution for intrepid.

right now I use vesa driver and do not thing with tvtime etc.

```
 lspci -nn | grep VGA 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:9490]

```

```
glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project
```

Thank you

---

### Post by excogitation on 2008-10-04
You can use the Ati opensource drivers (xserver-xorg-video-ati) - but you have to completely remove the fglrx drivers to make those work.

Try searching if you can't make it work.

---

### Post by isrich on 2008-10-04
> **excogitation said:**
> You can use the Ati opensource drivers (xserver-xorg-video-ati) - but you have to completely remove the fglrx drivers to make those work.

Try searching if you can't make it work.

It say 
```
(EE) No deivce detected
```
:(

---

### Post by BwackNinja on 2008-10-05
based on what phoronix says, it only works with a modified driver, so you'd have to edit the source and compile or get someone to do it for you. If I can find out how, I can do it for you. (also - it doesn't work with a DVI connection)

---

### Post by isrich on 2008-10-05
> **BwackNinja said:**
> based on what phoronix says, it only works with a modified driver, so you'd have to edit the source and compile or get someone to do it for you. If I can find out how, I can do it for you. (also - it doesn't work with a DVI connection)

Thank you

That what I heard from phoronix and what I looking for too.
I'd been search for modification method for a while but found not thing. 
Can you guild me a "how to" documents ?

---

### Post by waspbr on 2008-10-05
I guess I have a similar problem, I have an radeon HD 3850 AGP on a 32 bit box running 2.6.27-5  and still no cake witht he graphics drivers. Envy does not work, it crashed everytime I try to open it. Oddly enough even my laptop (64bit) with nvidia drivers can not seem to run envy. 

Everytime I try to enable my the driver in the "hardware driver" gui I get 

```
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid.
```

Which to some extent makes sense, since intrepid would not produce a working xorg but I had to build mine manually (based on my hardy partition install)

if anyone is interested here's my xorg

```
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Module"
	Load		"dri"
	Load		"glx"
EndSection

Section "Device"
	Identifier	"ATI Radeon HD 3850"
	Driver		"vesa"
	Option		"XaaNoOffscreenPixmaps"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod"		"EXA"
	Option 		"AGPMode" 		"1"
	Option 		"AGPFastWrite" 		"1"
	Option 		"AccelDFS" 		"off"
	Option		"MigrationHeuristic"	"greedy"
	Option		"DRI"			"true"
	Option		"TexturedVideo"		"on"
	Option		"UseFastTLS"		"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"ForceGenericCPU"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
thanks for the help

oh yeah, it won't boot unless I choose put "vesa" in the driver slot

---

### Post by wgrant on 2008-10-05
> **waspbr said:**
> 
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

You have no "Configured Video Device". That's why it fails.

---

### Post by waspbr on 2008-10-05
thanks I'll give that a shot

---

### Post by waspbr on 2008-10-05
The good news is that now I can open the hardwre drivers, tho when I click on activate it posts a message saying that jockey-gtk just crashed...

sigh... I guess I just have to wait for the updates.

update: actually the ati drivers are not even listed

---

### Post by BwackNinja on 2008-10-05
@waspbr
As it was said before, fglrx (the closed-source ati drivers) don't yet work in intrepid. The open-source drivers work well for most though. They require completely removing fglrx first though. Another thread here on the ati drivers tells you how.

@isrich
I'll mess around with the source and see if I'll be able to guide you through it. The place where the modifications go shouldn't be too hard to find.

EDIT:
[http://lists.opensuse.org/radeonhd/2007-12/msg00267.html](http://lists.opensuse.org/radeonhd/2007-12/msg00267.html) fairly clearly defines how to do this with the radeonhd driver (if you know how to read diffs :P) I've got a bit of work to do, but I should be able to guide you through this today if someone doesn't beat me to it.

---

### Post by krazyd on 2008-10-05
> **lewmnik said:**
> Radeon does not work on amd64... Here's hoping the linux dude is right :confused:
Radeon driver works out of the box on amd64 here.. :KS

---

### Post by ktp on 2008-10-05
Same here...using the Radeon/ati open source drivers on amd64.

---

### Post by quazar on 2008-10-05
I have been struggeling with xorg.conf for some hours in order to get compiz running in Ibex with my HD3200. No luck so far unfortunately. 


```
$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1360x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```

[HTML]$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
[/HTML]

```
$ glxgears
902 frames in 5.0 seconds = 180.292 FPS
1104 frames in 5.0 seconds = 220.627 FPS
1072 frames in 5.0 seconds = 214.326 FPS

```

```
Section "Module"
	Load		"dri"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "ati"
        Option          "AccelMethod"   	"EXA"
        Option          "AccelDFS"      	"true"
        Option          "AGPMode"       	"8"
        Option          "AGPFastWrite"  	"1"
#        Option		"EnablePageFlip"	"true"
        Option 		"ColorTiling"		"on"
	Option          "GARTSize" 		"64"
	Option          "DRI"			"true"
	Option 		"XAANoOffscreenPixmaps" "true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"EnablePageFlip"	"true"
	Option          "DMAForXv"       	"true"
	Option          "TripleBuffer"   	"true" 
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"        
EndSection


Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option 		"Composite" "Enable"
EndSection


Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

Section "ServerFlags"
   	Option 		"IgnoreABI" "True"
EndSection
```

Removing some options from xorg.conf does not help. I dont know what im doing wrong...

edit:
```
$ SKIP_CHECKS=yes compiz --replace
```
result in a white screen with only the cursor, so Compiz is clearly not working

---

### Post by murmel on 2008-10-05
I'm using the ATI X2300 and the open source drivers works fine but looks like direct rendering doesn't work..
```
glxinfo | grep direct
Output: direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```

I've tried installing the latest ati-drivers but without success.. GDM stays black and looks like it doesn't starts at all..
```
mkdir ati-driver
cd ati-driver
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-9-x86.x86_64.run
sudo -s
sh ati-driver-installer-8-9-x86.x86_64.run --buildpkg Ubuntu/intrepid
dpkg -i *.deb
depmod -a
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak_01
aticonfig --initial
aticonfig --overlay-type=Xv
shutdown -hr now
```

Anybody got some tips?

---

### Post by excogitation on 2008-10-05
> **isrich said:**
> It say 
```
(EE) No deivce detected
```
:(

I'm sorry I didn't check before - but
it seems your card isn't supported by the open source driver (yet?).
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by BwackNinja on 2008-10-05
> **excogitation said:**
> I'm sorry I didn't check before - but
it seems your card isn't supported by the open source driver (yet?).
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Not officially, but its known to work with both radeon and radeonhd open-source drivers by adding the PCI ID. A simple addition and compile is easy and can be done on another computer too. iirc, it is only one file generated. The only thing is that I can't guarantee compiz will work, but most stuff will and compiz might.

---

### Post by krazyd on 2008-10-06
> **quazar said:**
> I have been struggeling with xorg.conf for some hours in order to get compiz running in Ibex with my HD3200. No luck so far unfortunately...
> **murmel said:**
> I'm using the ATI X2300 and the open source drivers works fine but looks like direct rendering doesn't work..
Anybody got some tips?
Your cards are currently not supported by the open source driver for 3d / video. It is being actively worked on however ;)

Only cards up to the X1950 (R500 series) are currently supported.

---

### Post by sstefan on 2008-10-06
Hello,

I tried Xubuntu 8.10 on my m2r32 (Amd 580 Chipset) with an Ati x1950pro.
The X-Server doesn`t start and due to the fact that Ubuntu doens`t have a text-installer it is impossible to install it.
Configuring /etc/X11/xorg.conf won`t help, Ubuntu configures it on-the-fly. Any ideas?

---

### Post by krazyd on 2008-10-06
ubuntu does have a text installer: it's the 'alternate' disc, instead of the 'desktop' disc to download

---

### Post by BwackNinja on 2008-10-06
@isrich
I got the hang of patching the radeon driver adding the pci id. Are you interested?

---

### Post by camtech on 2008-10-07
Would the HD3850 be in the same category as the 48xxs driver-wise? Or what is recommended for this card so far (64bit)?

---

### Post by krazyd on 2008-10-07
> **camtech said:**
> Would the HD3850 be in the same category as the 48xxs driver-wise?
Pretty much I'm afraid..
> **camtech said:**
> Or what is recommended for this card so far (64bit)?
The open-source driver can do mode-setting (so you'll get the right resolution etc.) just not 3d or video acceleration. I'm not sure what the status of fglrx is with the xserver version in intrepid..

---

### Post by murmel on 2008-10-08
Looks like direct rendering works now. After the latest update!
```
murmel@murmel-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
[...]
```

Sweet!
But I wonder when ATI-drivers will work.

Edit:
Nexuiz, OpenArena and Alien-Arena barely works. Can't nearly move the mouse! :/

---

### Post by isrich on 2008-10-09
Hi 
sorry for disappear for couple days. :(

> **BwackNinja]
EDIT:
[http://lists.opensuse.org/radeonhd/2.../msg00267.html](http://lists.opensuse.org/radeonhd/2.../msg00267.html) fairly clearly defines how to do this with the radeonhd driver (if you know how to read diffs :P) I've got a bit of work to do, but I should be able to guide you through this today if someone doesn't beat me to it.
[/QUOTE]
Thank you for useful information.  

[QUOTE=BwackNinja said:**
> @isrich
I got the hang of patching the radeon driver adding the pci id. Are you interested?
Yes, of course :) 

[QUOTE=BwackNinja]
Not officially, but its known to work with both radeon and radeonhd open-source drivers by adding the PCI ID. A simple addition and compile is easy and can be done on another computer too. iirc, it is only one file generated. The only thing is that I can't guarantee compiz will work, but most stuff will and compiz might.[/QUOTE]

I am know a little bit 'bout compiling + src tree in debian but I can try. If I find some documents about it. 
English is not my native language so I did not even know what is "key word" I'd use for googling. :(

compiz not my option right now I can live without it :)

---

### Post by murmel on 2008-10-15
Looks like it works now!
```
murmel@murmel-laptop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
[...]
client glx vendor string: SGI
client glx version string: 1.4
[...]
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X2300
OpenGL version string: 2.1.8087 Release
OpenGL shading language version string: 1.20
[...]
```

Just updated today and activated the restricted driver. ! =)
Woho!

---

### Post by Dauthi4 on 2008-10-15
I've activated the restricted driver too, using jokey and the result is :

```
glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Any ideas ?

---

### Post by isrich on 2008-10-15
Yes It'd done this afternoon(+7), Now I a happy man. :guitar:

> @ibex-b-1:~$ glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: ATI Radeon HD 4670

and this
> @ibex-b-1:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4670
OpenGL version string: 2.1.8087 Release


By now try to update and update-manager told me it will remove xorg-driver-fglrx, What dos it mean?  

still did not tried with tvtime :(

---

### Post by helliewm on 2008-10-15
See my post new Beta ATI Catalyst DRivers have literally just come into the Intrepid Repostiories.

Full instructions are here:

[http://ubuntuforums.org/showthread.php?t=948529]("http://ubuntuforums.org/showthread.php?t=948529") 

Helen

I made a new post so it could be easily seen.

---

### Post by inportb on 2008-10-15
> **Dauthi4 said:**
> I've activated the restricted driver too, using jokey and the result is :

```
glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Any ideas ?

Have you got *Driver "fglrx"* in your xorg.conf's *Device* section?

---

### Post by Dauthi4 on 2008-10-22
> **inportb said:**
> Have you got *Driver "fglrx"* in your xorg.conf's *Device* section?

Yes and always the same problem, fglrx module seems to be loaded 

```
lsmod | grep fglrx
fglrx                1555468  0 
agpgart                34760  2 fglrx,ati_agp

```

and Xorg.log tells

```
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(II) fglrx(0): detected X.org 7.4.2.0
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
```

I tried everything... :( (For the record, I have a Xpress 200 M)

---

### Post by taseedorf on 2008-10-27
I have the exact same issue and exact same card as you...it all came about when I upgrade to 8.10... THIS PAGE WILL HELP!

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Restricted_Drivers_Manager](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Restricted_Drivers_Manager)


:)

---

