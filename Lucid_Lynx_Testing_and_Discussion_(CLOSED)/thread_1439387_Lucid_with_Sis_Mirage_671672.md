---
title: "Lucid with Sis Mirage 671/672"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by andydch on 2010-03-26
I see problem when boot using lucid beta1 (in live usb). My screen is flickering.
My VGA card is Sis Mirage 671. Is Sis Mirage not supported in Lucid?
This problem is not showned with VGA card Intel.

Thanks

---

### Post by master2 on 2010-03-27
here too! i have a "SiS 771/671 Mirage 3" in my laptop and when i will boot from CD, its only flickering! cant see anything. ](*,) :sad:

---

### Post by MichealH on 2010-03-28
That is just Plymouth just wait and you should be on desktop/installer but this is annoying you even cant install karmic drivers! :@

---

### Post by jb_barroso on 2010-03-30
SiS M671/M672 driver for xorg xserver 7.5 on Debian / Sidux (Working on Ubuntu 10.04):

[http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/](http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/)

---

### Post by andydch on 2010-04-05
how to install this driver?
i can't see login page... :(

---

### Post by MichealH on 2010-04-05
Install it by coptin the .so and .la file to /usr/lib/xorg/modules/drivers and then generate a xorg.conf and add in Device ```
Driver "sis671
``` For the plymouth thing do the thing in this post : [http://ubuntuforums.org/showpost.php?p=9078857&postcount=10](http://ubuntuforums.org/showpost.php?p=9078857&postcount=10)

---

### Post by andydch on 2010-04-06
> **MichealH said:**
> Install it by coptin the .so and .la file to /usr/lib/xorg/modules/drivers and then generate a xorg.conf and add in Device ```
Driver "sis671
``` For the plymouth thing do the thing in this post : [http://ubuntuforums.org/showpost.php?p=9078857&postcount=10](http://ubuntuforums.org/showpost.php?p=9078857&postcount=10)

Hi Michel,

I boot using live usb. When booting processing, the screen is flickering and after 5 minutes still flickering so I can't see nothing. Any trick so I can try your suggestion above?

---

### Post by MichealH on 2010-04-06
> **andydch said:**
> Hi Michel,

I boot using live usb. When booting processing, the screen is flickering and after 5 minutes still flickering so I can't see nothing. Any trick so I can try your suggestion above?

If you wait until desktop shows up do what I said for Plymouth above it should write the changes.

---

### Post by andydch on 2010-04-07
> **MichealH said:**
> If you wait until desktop shows up do what I said for Plymouth above it should write the changes.

until 30minutes my screen still flickering
how long i have to wait until desktop shows up?

---

### Post by MichealH on 2010-04-07
It shouldn't take that long... Try Re-burning the .iso at the lowest possible speed and see If that fixed the "no boot" problem.

Oh and try burning it on a CD

---

### Post by andydch on 2010-04-09
Hi MichealH,

I have reburned ISO on CD and then boot with it. Same like before. Screen still flickering and desktop does not show up. :(

The ISO is ubuntu beta 2.

---

### Post by master2 on 2010-04-09
same.. beta 2 only flickering... ](*,) ](*,) ](*,) ](*,)

[COLOR=Red]**PLEASE ADD SUPPORT FOR SIS IN THE NEXT RELEASE!**[/COLOR]

---

### Post by MichealH on 2010-04-10
> **andydch said:**
> Hi MichealH,

I have reburned ISO on CD and then boot with it. Same like before. Screen still flickering and desktop does not show up. :(

The ISO is ubuntu beta 2.

Could you post a picture for refernce/solution

> **master2 said:**
> same.. beta 2 only flickering... ](*,) ](*,) ](*,) ](*,)

[COLOR=Red]**PLEASE ADD SUPPORT FOR SIS IN THE NEXT RELEASE!**[/COLOR]

They cant If i remember there is no open-source driver it is proprietary and can be added

---

### Post by master2 on 2010-04-10
[COLOR=YellowGreen]**ITS WORKING WITH SiS 771/671 Mirage 3!!**[/COLOR] im using ubuntu 10.04 beta 2, release 10.04.2010


1. boot from cd

then comes this:
[[IMG]http://www.abload.de/thumb/img_0027pjxh.jpg[/IMG]]("http://www.abload.de/image.php?img=img_0027pjxh.jpg")

2. **wait ca. 5 minutes and do nothing!**

3. then comes the installer with 800x600 without flickering! ):P


now i most searching for driver that support higher solution... :confused:

---

### Post by MichealH on 2010-04-10
Driver for 1280x800 SiS Mirage 3 screens : [http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz]("http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz")

Extract sis671.la and sis671.so to /usr/lib/xorg/modules/drivers and the xorg.conf to /etc/X11.

This is the Plymouth solution:

> the solution is easy; 
open a terminal;
become root
```
sudo bash
```
type;
```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```
type;
```
update-initramfs -u
```
```
reboot
```
Everything is working like a charm.

---

### Post by master2 on 2010-04-10
**edit**... see #23 for solution

---

### Post by clhsharky on 2010-04-10
HI 

On Sis chips I use the Alternate install cd.
Install.
Restart, update at command line, or low graphics mode.
Install or check to see if correct driver was installed.
Restart.

Even on Karmic I've had that video corruption with SiS on install.


Sharky

---

### Post by saliflo on 2010-04-10
THANK YOU VERY MUCH. It works perfectly

---

### Post by mhgsys on 2010-04-10
I've made the same post here: [http://www.uluga.ubuntuforums.org/showthread.php?t=958967&page=37](http://www.uluga.ubuntuforums.org/showthread.php?t=958967&page=37)
and I can only suggest to all have this talk there; since that's an active thread on the sis 771/671
 anyway; since there's gonna be same discussion on this page; also posting it here

[COLOR=Red][B]THIS WORKS on ubuntu 10.04__
[/B][/COLOR]
I've just installed ubuntu 10.04 on my belinea c1541 laptop, which also has a sis 771/671
@MichealH ..read below.. plymouth solution is on the bottom of this text.

Anway; I've used the drivers from [http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/](http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/)

take the install files, unzip them
once unzipped copy or move them (I just copied them) *in terminal go to the path you've unzipped them in f.e; cd /home/user/Downloads

```
sudo cp sis671_drv.* /usr/lib/xorg/modules/drivers/
```Then I generated a xorg.conf.
I opened up a terminal and typed;
```
sudo service gdm stop
```**Then switching to tty**1 which had only scrambled text.
Anyway; logged in blindly
became root with
```
sudo bash
```then generated a xorg.conf file with
```
Xorg -configure
```started gdm again with
```
service gdm start
```Opened up a terminal again;
moved the autogenerated xorg.conf.new to /etc/X11/xorg.conf
```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```and restarted gdm again;
```
sudo service gdm restart
```I now have a very nice workable screen. )(1280x800)

Then I noticed the plymouth problem and the fact all tty's were still scrambled. 
However; the solution is easy; 
open a terminal;
become root
```
sudo bash
```type;```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```type;
```
update-initramfs -u
``````
reboot
```Everything is working like a charm.

---

### Post by lulacLilla on 2010-04-10
I have the same problem on my generic laptop, installed ubuntu 10.04 beta and the best resolution available is 800x600. At the start-up there are purple lines flickering as mentioned in the first post.

MHGSYS can you please provide "an idiot's guide" how to solve this issue. I tried what you wrote but still no joy. I don't know what you mean by switching to TTY.

thank you,
navy

---

### Post by andydch on 2010-04-10
after wait until 10 minutes, it works! desktop shows up... :guitar:

thanks michealh... :)

---

### Post by mhgsys on 2010-04-10
> **lulacLilla said:**
> I have the same problem on my generic laptop, installed ubuntu 10.04 beta and the best resolution available is 800x600. At the start-up there are purple lines flickering as mentioned in the first post.

MHGSYS can you please provide "an idiot's guide" how to solve this issue. I tried what you wrote but still no joy. I don't know what you mean by switching to TTY.

thank you,
navy

**Sure**;

[COLOR=Blue][B][SIZE="3"]THIS WORKS on ubuntu 10.04 explained version[/SIZE] __
[/B][/COLOR]

[B]download the drivers from [http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/](http://estebanordano.com.ar/sis-m671m672-driver-for-xorg-xserver-7-5-on-debian-sidux/)
(take the install files), unzip them
[/B]
once unzipped copy or move them (I just copied them)

**Open up a terminal and go to the path you've unzipped them in**.(use the cd command to navigate to directory's)** f.e; cd /home/user/Downloads**

```
sudo cp sis671_drv.* /usr/lib/xorg/modules/drivers/
``` 

**then stop X**

```
sudo service gdm stop
``` 
**you'll have to do next part blindly)**

(We need to stop X or we won't be able to auto-generate a xorg.conf.new

```
Switch to tty1 by pressing Ctrl+Alt+f1
``` (f2 for tty2, f3 for tty3, etc.. (f7 should be X)

**Even though you won't be able to read it (yet) you can login**
```
type in your username and press enter
```
```
type in your password and press enter
```

**Now you're logged in you want to become root; **type;
```
sudo bash
```
```
type in your password
```

**Now your root; type in**
```
Xorg -configure
```
[B](this will create a xorg.conf.new in your home directory)
[/B]
**and start gdm again with**
```
service gdm start
```
Once there; Open up a terminal again;
[B]move the auto-generated xorg.conf.new to /etc/X11/xorg.conf
with[/B]
```
sudo mv xorg.conf.new /etc/X11/xorg.conf
```a**nd restart gdm by typing;**
```
sudo service gdm restart
```

[B]Fix the plymouth and the unreadable tty problem like this:
Open up a terminal and typ
[/B]
```
sudo bash
```
```
 enter your password
```

**type;**```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```type;
```
update-initramfs -u
```
[B]and reboot 
[/B]
```
reboot
```[SIZE="3"][/SIZE]

---

### Post by master2 on 2010-04-10
**mhgsys**
your soultion dont working by me. when i shutdown the gdm, its only flickering...


**[COLOR=Lime][SIZE=4]..but here is a working soultion (SiS 771/671 Mirage 3 and ubuntu 10.04 beta 2, release 10.04.2010)[/SIZE][/COLOR]**

1. boot from cd. it will be flickering like this:
[[IMG]http://www.abload.de/thumb/img_0027pjxh.jpg[/IMG]]("http://www.abload.de/image.php?img=img_0027pjxh.jpg")

wait few minutes and the ubuntu installer lookup with 800x600.

2. install ubuntu

3. download and extract this:
[http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz](http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz)
MIRROR: [http://uploaded.to/file/o4x6dd](http://uploaded.to/file/o4x6dd)

4. copy the **sis671.la** and the **sis671.so** to

```
/usr/lib/xorg/modules/drivers
```

5. copy the **xorg.conf** to

```
/etc/X11
```

6. reboot your machine

7. open a terminal and enter this commands:

```
sudo bash
```
*(enter passwort...)*
```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```
```
update-initramfs -u
```

8. reboot your machine again.

thats it!

[[IMG]http://www.abload.de/thumb/bildschirmfotol62q.png[/IMG]]("http://www.abload.de/image.php?img=bildschirmfotol62q.png")

thanks for all helpers...

---

### Post by mhgsys on 2010-04-10
@master2

The biggest difference would be the xorg.conf included in your download; (and rebooting instead of just restarting X/gdm:   lol)

..btw, you better reboot after you just fresh installed ubuntu  or you would be still running live cd, trying to include drivers on that.... 

Anyway;I wonder if that xorg.conf is multi compatible. (edit: tested it; your xorg.conf also works.,) 

**still I rather auto-generate  **
(I like my 2d support... dri ,glx etc)

Compared; 
**The provided xorg.conf in your link**
```
 Section "Monitor"
    Identifier "PBMonitor"
EndSection

Section "Device"
    Identifier "SIS 671"
    Driver "sis671"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "SIS 671"
    Monitor "PBMonitor"
EndSection

```

**My xorg.conf** (auto-generated)
```
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
	Load  "dbe"
	Load  "extmod"
	Load  "record"
	Load  "dri2"
	Load  "glx"
	Load  "dri"
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

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "FastVram"           	# [<bool>]
        #Option     "HostBus"            	# [<bool>]
        #Option     "BenchmarkMemcpy"    	# [<bool>]
        #Option     "UseSSE"             	# [<bool>]
        #Option     "MaxXFBMem"          	# <i>
        #Option     "Accel"              	# [<bool>]
        #Option     "TurboQueue"         	# [<bool>]
        #Option     "RenderAcceleration" 	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "AGPSize"            	# <i>
        #Option     "GARTSize"           	# <i>
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "Reflect"            	# <str>
        #Option     "EnableSiSCtrl"      	# [<bool>]
        #Option     "SWCursor"           	# [<bool>]
        #Option     "HWCursor"           	# [<bool>]
        #Option     "ColorHWCursor"      	# [<bool>]
        #Option     "UseColorHWCursor"   	# [<bool>]
        #Option     "ColorHWCursorBlending" 	# [<bool>]
        #Option     "ColorHWCursorBlendThreshold" 	# <i>
        #Option     "InternalModes"      	# [<bool>]
        #Option     "ConstantDPI"        	# [<bool>]
        #Option     "OverruleFrequencyRanges" 	# [<bool>]
        #Option     "RestoreBySetMode"   	# [<bool>]
        #Option     "Vesa"               	# [<bool>]
        #Option     "ForceCRT1Type"      	# <str>
        #Option     "ForceCRT1"          	# [<bool>]
        #Option     "ForceCRT2Type"      	# <str>
        #Option     "CRT2Detection"      	# [<bool>]
        #Option     "CRT1LCD"            	# [<bool>]
        #Option     "ForceCRT2ReDetection" 	# [<bool>]
        #Option     "EnableHotkey"       	# [<bool>]
        #Option     "ForceCRT1VGAAspect" 	# <str>
        #Option     "ForceCRT2VGAAspect" 	# <str>
        #Option     "UseROMData"         	# [<bool>]
        #Option     "UseOEMData"         	# [<bool>]
        #Option     "ScaleLCD"           	# [<bool>]
        #Option     "CenterLCD"          	# [<bool>]
        #Option     "PanelDelayCompensation" 	# <i>
        #Option     "PDC"                	# <i>
        #Option     "PanelDelayCompensation2" 	# <i>
        #Option     "PDC2"               	# <i>
        #Option     "PanelDelayCompensation1" 	# <i>
        #Option     "PDC1"               	# <i>
        #Option     "EMI"                	# <i>
        #Option     "LVDSHL"             	# <i>
        #Option     "ForcePanelRGB"      	# <i>
        #Option     "SpecialTiming"      	# <str>
        #Option     "TVStandard"         	# <str>
        #Option     "TVXPosOffset"       	# <i>
        #Option     "TVYPosOffset"       	# <i>
        #Option     "SISTVEdgeEnhance"   	# <i>
        #Option     "SISTVAntiFlicker"   	# <str>
        #Option     "SISTVSaturation"    	# <i>
        #Option     "SISTVCFilter"       	# [<bool>]
        #Option     "SISTVYFilter"       	# <i>
        #Option     "SISTVColorCalibFine" 	# <i>
        #Option     "SISTVColorCalibCoarse" 	# <i>
        #Option     "SISTVXScale"        	# <i>
        #Option     "SISTVYScale"        	# <i>
        #Option     "SenseYPbPr"         	# [<bool>]
        #Option     "YPbPrAspectRatio"   	# <str>
        #Option     "TVBlueWorkAround"   	# [<bool>]
        #Option     "CHTVType"           	# [<bool>]
        #Option     "CHTVOverscan"       	# [<bool>]
        #Option     "CHTVSuperOverscan"  	# [<bool>]
        #Option     "CHTVLumaBandwidthCVBS" 	# <i>
        #Option     "CHTVLumaBandwidthSVIDEO" 	# <i>
        #Option     "CHTVLumaFlickerFilter" 	# <i>
        #Option     "CHTVChromaBandwidth" 	# <i>
        #Option     "CHTVChromaFlickerFilter" 	# <i>
        #Option     "CHTVCVBSColor"      	# [<bool>]
        #Option     "CHTVTextEnhance"    	# <i>
        #Option     "CHTVContrast"       	# <i>
        #Option     "SIS6326TVAntiFlicker" 	# <str>
        #Option     "SIS6326TVEnableYFilter" 	# [<bool>]
        #Option     "SIS6326TVYFilterStrong" 	# [<bool>]
        #Option     "SIS6326TVForcePlug" 	# <str>
        #Option     "SIS6326FSCAdjust"   	# <i>
        #Option     "CRT1Gamma"          	# [<bool>]
        #Option     "CRT2Gamma"          	# [<str>]
        #Option     "GammaBrightness"    	# <str>
        #Option     "GammaBrightnessCRT2" 	# <str>
        #Option     "CRT2GammaBrightness" 	# <str>
        #Option     "Brightness"         	# <str>
        #Option     "NewGammaBrightness" 	# <str>
        #Option     "CRT2Brightness"     	# <str>
        #Option     "CRT2NewGammaBrightness" 	# <str>
        #Option     "Contrast"           	# <str>
        #Option     "NewGammaContrast"   	# <str>
        #Option     "CRT2Contrast"       	# <str>
        #Option     "CRT2NewGammaContrast" 	# <str>
        #Option     "CRT1Saturation"     	# <i>
        #Option     "Xvideo"             	# [<bool>]
        #Option     "XvOnCRT2"           	# [<bool>]
        #Option     "XvGamma"            	# [<str>]
        #Option     "XvDefaultContrast"  	# <i>
        #Option     "XvDefaultBrightness" 	# <i>
        #Option     "XvDefaultHue"       	# <i>
        #Option     "XvDefaultSaturation" 	# <i>
        #Option     "XvDefaultDisableGfx" 	# [<bool>]
        #Option     "XvDefaultDisableGfxLR" 	# [<bool>]
        #Option     "XvChromaMin"        	# <i>
        #Option     "XvChromaMax"        	# <i>
        #Option     "XvUseChromaKey"     	# [<bool>]
        #Option     "XvInsideChromaKey"  	# [<bool>]
        #Option     "XvYUVChromaKey"     	# [<bool>]
        #Option     "XvDisableColorKey"  	# [<bool>]
        #Option     "XvDefaultAdaptor"   	# <str>
        #Option     "YV12"               	# [<bool>]
        #Option     "MergedFB"           	# [<str>]
        #Option     "TwinView"           	# [<str>]
        #Option     "MergedFBAuto"       	# [<bool>]
        #Option     "CRT2HSync"          	# <str>
        #Option     "SecondMonitorHorizSync" 	# <str>
        #Option     "CRT2VRefresh"       	# <str>
        #Option     "SecondMonitorVertRefresh" 	# <str>
        #Option     "CRT2Position"       	# <str>
        #Option     "TwinViewOrientation" 	# <str>
        #Option     "MetaModes"          	# <str>
        #Option     "MergedDPI"          	# <str>
        #Option     "MergedXinerama"     	# [<bool>]
        #Option     "TwinviewXineramaInfo" 	# [<bool>]
        #Option     "MergedXineramaScreen0" 	# [<str>]
        #Option     "MergedXineramaCRT2IsScreen0" 	# [<bool>]
        #Option     "MergedNonRectangular" 	# [<bool>]
        #Option     "MergedMouseRestriction" 	# [<bool>]
        #Option     "FutroTiming"        	# [<bool>]
	Identifier  "Card0"
	Driver      "sis671"
	VendorName  "Silicon Integrated Systems [SiS]"
	BoardName   "771/671 PCIE VGA Display Adapter"
	BusID       "PCI:1:0:0"
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

```

---

### Post by VMC on 2010-04-10
> **lulacLilla said:**
> I have the same problem on my generic laptop, installed ubuntu 10.04 beta and the best resolution available is 800x600. At the start-up there are purple lines flickering as mentioned in the first post.

MHGSYS can you please provide "an idiot's guide" how to solve this issue. I tried what you wrote but still no joy. I don't know what you mean by switching to TTY.

thank you,
navy

I think what he's referring to is one of the VTY's (Ctrl+Alt+F1, for example). Another way is to boot into recovery mode , by adding "single" at the end of the linux boot line. Do this through boot boot menu.

---

### Post by mhgsys on 2010-04-11
> **lulacLilla said:**
> Thanks a lot mhgsys! Everything working perfectly now - crystal clear resolution, perfect. I owe you a beer if you ever come to Brazil:-)

That part done blindly was a bit scary for me as I'm still a beginner but another day another learning curve.

Thanks a again.

All of you who have the same problem just follow mhgsys's howto - it works!

Great, I'll like knowing to have a beer if I'm ever in brazil :)

Anyway; suggesting again to keep the sis 771 /671 talk in this thread
[http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)

---

### Post by MichealH on 2010-04-11
> **master2 said:**
> **mhgsys**
your soultion dont working by me. when i shutdown the gdm, its only flickering...


**[COLOR=Lime][SIZE=4]..but here is a working soultion (SiS 771/671 Mirage 3 and ubuntu 10.04 beta 2, release 10.04.2010)[/SIZE][/COLOR]**

1. boot from cd. it will be flickering like this:
[[IMG]http://www.abload.de/thumb/img_0027pjxh.jpg[/IMG]]("http://www.abload.de/image.php?img=img_0027pjxh.jpg")

wait few minutes and the ubuntu installer lookup with 800x600.

2. install ubuntu

3. download and extract this:
[http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz](http://dl.dropbox.com/u/983756/sis671_10.x.tar.gz)
MIRROR: [http://uploaded.to/file/o4x6dd](http://uploaded.to/file/o4x6dd)

4. copy the **sis671.la** and the **sis671.so** to

```
/usr/lib/xorg/modules/drivers
```

5. copy the **xorg.conf** to

```
/etc/X11
```

6. reboot your machine

7. open a terminal and enter this commands:

```
sudo bash
```
*(enter passwort...)*
```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```
```
update-initramfs -u
```

8. reboot your machine again.

thats it!

[[IMG]http://www.abload.de/thumb/bildschirmfotol62q.png[/IMG]]("http://www.abload.de/image.php?img=bildschirmfotol62q.png")

thanks for all helpers...

Thanks for thanking me :D Good job I got those drivers in the .tar.gz I always put them in Dropbox so I can set my computer up again... I have lots of scripts in there. I might just make a script for that :lolflag:

---

### Post by mhgsys on 2010-04-11
[COLOR="Red"][B][SIZE="3"]Don't you people read?

As I was saying before; you A; should reboot ubuntu first after installing it;

and B:
the xorg.conf provided by that link won't give you 2d support; as dri and glx are not loaded at all.

It's good you want to help people by creating an easier way; but I don't really like the fact you (michaelh and master2) are pretending to have found the solution yourself .

As anyone can see; you are the same people as who did not understand my "howto" before. 

[http://ubuntuforums.org/showthread.php?t=958967&page=37](http://ubuntuforums.org/showthread.php?t=958967&page=37)

So please; at least edit the howto you people made to be a working one. 
And stop trying to gain credit with other peoples work.[/SIZE][/B][/COLOR]

---

### Post by MichealH on 2010-04-11
> **mhgsys said:**
> [noparse][COLOR="Red"][B][SIZE="3"]Don't you people read?

As I was saying before; you A; should reboot ubuntu first after installing it;

and B:
the xorg.conf provided by that link won't give you 2d support; as dri and glx are not loaded at all.

It's good you want to help people by creating an easier way; but I don't really like the fact you (michaelh and master2) are pretending to have found the solution yourself .

As anyone can see; you are the same people as who did not understand my "howto" before. 

[http://ubuntuforums.org/showthread.php?t=958967&page=37](http://ubuntuforums.org/showthread.php?t=958967&page=37)

So please; at least edit the howto you people made to be a working one. 
And stop trying to gain credit with other peoples work.[/SIZE][/B][/COLOR][/noparse]

The only thing I got was the plymouth thing not the drivers I had put them in the tar myself along with a few mods.

---

### Post by mhgsys on 2010-04-11
> **MichealH said:**
> The only thing I got was the plymouth thing not the drivers I had put them in the tar myself along with a few mods.

Ok, maybe I came over a little to harsh.. Let me explain myself;

What I mean by it; is that you just both look over the fact I've pointed out that the "solution master2 wrote" **contains errors**, **misses direct commands** and that the xorg.conf which you included in your link[B] misses things like dri and glx
Meaning missing Direct Rendering and missing 2d support.[/B]

My "howto" contains the way to generate a xorg.conf.new which includes all these "needed" options, (as you can see on my generated xorg.conf)


It would have been better if you just linked people to the post I wrote on [http://ubuntuforums.org/showthread.php?t=958967&page=38](http://ubuntuforums.org/showthread.php?t=958967&page=38)
as I said before; That's the most active thread on the sis 771/671 and contains lot's of users which have all contributed to make the sis work since 2008

btw. @master2.. From the beginning > I clearly stated you'll have to log in blindly on tty.. I even wrote it in **bold** in the explained /"idiot" version I wrote
 :mrgreen:

---

