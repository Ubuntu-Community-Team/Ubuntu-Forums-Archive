---
title: "No X display after system update"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wikid_one on 2008-10-06
I'm running intrepid on my laptop, and hadn't updated in at least a couple weeks.  There were over 150 updates that were installed, but I didn't look at the list to see what they were.  There were a bunch of them and I just hit OK.  After a reboot, I have no display.  I have sounds, and I can log in... so I know X is working.  I'm assuming that it is somethign with my video card driver (ATI Mobile HD4500).  How do I determine what my problem is?

---

### Post by overdrank on 2008-10-06
> **wikid_one said:**
> I'm running intrepid on my laptop, and hadn't updated in at least a couple weeks.  There were over 150 updates that were installed, but I didn't look at the list to see what they were.  There were a bunch of them and I just hit OK.  After a reboot, I have no display.  I have sounds, and I can log in... so I know X is working.  I'm assuming that it is somethign with my video card driver (ATI Mobile HD4500).  How do I determine what my problem is?


Moved :)

---

### Post by BwackNinja on 2008-10-06
posting your /var/log/Xorg.0.log would be nice.

---

### Post by waspbr on 2008-10-07
I am going to go on a limb here and assume that your problem is related to your xorg. I had a similar problem , could boot up to the gdm, I would even hear the ubuntu sounds but there would be nothing on the screen, it would turn itself off.

I would then access the command line by doing Ctrl+Alt+F1, then do a

```
sudo apt-get update
sudo apt-get upgrade
```

so everything would be up to date. 

to view/edit your xorg you can use nano

```
sudo nano /etc/X11/xorg.conf
```

the in the Device section enter the following line 

```
Driver  "vesa"
```

save and exit

this should allow you to boot, my guess is that the xorg is not being rebuilt correctly, beats me why.Actually it has to do with the incompatibility of the ati drivers with the new kernel, i think. Anyway you should be able to boot into your account then, 

I am gonna go ahead and post my xorg



```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Radeon HD 3850"
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
	#Option 		"AGPMode" 		"1"
	#Option 		"AGPFastWrite" 		"1"
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

I have an AGP card so I have commented out the relevant lines with a #, but the rest should be more or less similar (except u are using a 4850 and not a 3850). 

Hope this helps. The issues should be fixed when the new ati drivers are released

---

### Post by wikid_one on 2008-10-07
First off, I have a question... is it normal for Ubuntu to use an almost empty xorg.conf?  All I had in the file was this:

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

I was able to get the display to appear by using the vesa driver, but for the life of me I cannot get the screen resolution to change.  My screen resolution is currently 1400x1050, instead of the 1680x1050 it should be.  It just seems to be ignoring the mode lines that I enter.  I even tried changing it to 1024x768 and 800x600 with no luck.  I have pasted below my current xorg.conf file:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection      "Display"
                Depth   24
                Modes   "1680x1050"
        EndSubSection
EndSection
```

---

### Post by waspbr on 2008-10-07
it's is not common for the xorg to be this empty as far as I know, it is just not building itself correctly.

for more xorg editing info check
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by dabl on 2008-10-07
> **wikid_one said:**
> First off, I have a question... is it normal for Ubuntu to use an almost empty xorg.conf?  All I had in the file was this:

Yes, that's the "new normal".

If you can reboot into Recovery Mode, and choose the "Fix X" script, and then "Continue Normal Boot", it might straighten out the problem.

Maybe.  :)

---

### Post by wikid_one on 2008-10-07
Well, I was able to get my screen resolution to appear correctly.  I uninstalled the fglrx module, and I'm using the radeon one now.  Everything seems to be working fine, except for the earth-shattering 195 FPS i'm pulling in glxgears!  Oh well.  I only use the laptop for my school work and the occasional flash game, so I'm not worried about it.  Hopefully they will have everythign worked out here in the near future.  I'd really like to get compiz running.  I hate not being able to use my mouse wheel to switch desktops.

Thanks for your help everyone.

---

### Post by tilapia on 2008-10-07
Thanks, dabl. I had a very similar problem with Xorg failing and booting into recovery mode and running the fix X script worked a treat. Cheers!

---

### Post by tilapia on 2008-10-07
Tell a lie... No, it's still the same after rebooting.

---

### Post by UeB on 2008-10-08
Hallo

I have the same Problem

I installed ubuntu 8.10 alpha 5 wenn it was released

yesterday I upgrade all packages (the first time since I installed from CD)

now the moment x starts the sceen gets black ans stays black and no error mesg is displayed.
I can hear the sound that comes when one should tye the login name / password

I can even type it in (blind) and the I can the the hard disc working as if it would load the rest of the gnome desktop. But well the screen just stays black.

All other terminals work ( strg alt f1 and so one) nicely

I tryed adding the driver vesa statement to the xorg.conf (which is also nearly totally emty)
But the the xserver does not load compleatly the a blinking underscore sign is the the top.


I have an ATI Mobility Radeon HD 3450

---

### Post by dabl on 2008-10-08
> **tilapia said:**
> Tell a lie... No, it's still the same after rebooting.

There is some weirdness going on with the way X starts, lately. Sometimes "startx" at the user text prompt works fine, when it fails to start at boot.  Sometimes stopping KDM with ```
sudo /etc/init.d/kdm stop
``` and then rebooting into Recovery Mode, running "Fix X" and then continuing seems to take care of it.

---

### Post by manoharanm on 2008-10-08
I'm having a similar issue.   After the update yesterday (10/07/08), my kubuntu wouldn't boot.  It gets stuck @ the terminal prompt.   Started a thread elsewhere, but thought posting here might help.

I had installed the beta of Intrepid and using it for a few days now. I had updated the kernel (and other items) that the update manager prompted me with yesterday and Kubuntu wouldn't boot anymore. It stops at the terminal prompt and the gui doesn't load. I tried KDM start and get a message saying it is already started. I tried startx and saw some issues with the RADEON driver (or something related to RADEON)

kinit: No resume image, doing normal boot...
stops at command prompt (terminal)
following error observed in the error log

(II) RADEONHD(0): Mapped IO at 0xb7abb000
(II) RADEONHD(0): Mapped FB at 0xa7a4e000
Saw signal 11. Server aborting.
kernel 2.6.27-6

Everything was running fine till kernel 2.6.27-4; error started with yesterday's update (kernel 2.6.27-5). I rebuilt Kubuntu late yesterday using my ISO image (Intreprid beta) and everything was working okay until i thought i'll try my luck with the updates today. Once upgraded, I see the same error today.

My config:
Gateway m6862 laptop
Intel Core2Duo T5750 2.0 GHz
4 GB RAM
ATI Mobility Radeon HD 2600
Dual boot with Vista

---

### Post by Brickedin21 on 2008-10-18
i have the same issue, although i tried doing control alt f1 then doing sudo /etc/init.d/kdm stop   but it wouldnt take and it didnt work. so i still have no display. the control alt f1 seems fine, then after i tried that a couple times i rebooted the machine and ran fix x in recovery mode and still nothing. not sure what else to do... any help?



got a toshiba A305-S6898
Radeon HD 3470 video card


Thanks

---

### Post by timjohn7 on 2008-10-19
Similar problem... Kubuntu 8.10 Beta... boots to initial splash screen with HDD, System Tools, Globe & K Icons and then the screen goes blank.  No access to tty1,tty2 or tty7.
The new kernel seems to have done something unpleasant!
I have an Intel 82845G video card.

Any advice? :confused:

---

