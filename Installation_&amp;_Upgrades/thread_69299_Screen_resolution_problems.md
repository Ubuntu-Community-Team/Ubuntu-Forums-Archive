---
title: "Screen resolution problems"
date: 2005-09-26
forum: Installation &amp; Upgrades
---

### Post by cdouglas on 2005-09-26
I just installed 5.10preview, but I get a 640x480 resolution.  I tried to add to  /etc/X11/xorg.conf , by adding 
HorizSync 28-49
VertRefresh 43-72
I also changed those values a bit as I found them on other sites.
I am using a Dell Optiplex GX260 with a Dell E722p monitor.  I have XP on one partition, which I might add won't change screen resolution either.  I installed the driver for the monitor, but it didn't work.
Please help if you can, I'm at my wits end.

---

### Post by Teroedni on 2005-09-26
what resolution do you want?
With so low horinz sync and vertical sync you will get very low resolution

I think you should atleast be able to get 1024*768
try with
HorizSync 28-80
VertRefresh 43-90
and it should help

also you should have 1024*768 set as an option in  your modes selection

---

### Post by cdouglas on 2005-09-26
In the screen resolution tab, there is only one option, 640x480.
I tried to make the changes, but nothing changed.
Any other thoughts.
I really think it's weird that the res is so low on both XP and Ubuntu, and neither are letting me change it.

---

### Post by Teroedni on 2005-09-26
Where did you try to make the change???
Can you post your xorg file

do this If you use Ubuntu
Open Terminal 

copy this and paste in your terminal

sudo gedit /etc/X11/xorg.conf

You will get a text file

Copy all the text and paste it here

---

### Post by cdouglas on 2005-09-26
Unfortunately, I'm using my Mac to use the net.  I have no way to get that text to this machine to post.
This is what I did.

sudo -s -H
gedit /etc/X11/xorg.conf

Then I just added those values under Option "DPMS"
Then I saved the file, and restarted the PC.

Is there any specific stuff I can tell you, since I can't post the whole text file.

---

### Post by Teroedni on 2005-09-26
heres mine
You see i have take out the important


Section "Device"
	Identifier	"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nv"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-110
	VertRefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x960" "1200x900"  "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x960" "1200x900"  "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x960" "1200x900"  "1200x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x960" "1200x900"  "1200x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x960" "1200x900" "1200x800"  "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x960" "1200x900"  "1200x800"  "1024x768" "800x600" "640x480"
	EndSubSection
EndSection


if you see on the  subsection display you see i have a lot of differents modes
What have you got there?
you should atleast have this
SubSection "Display"
		Depth		24
		Modes	      "1024x768" "800x600" "640x480"

do you ?

---

### Post by cdouglas on 2005-09-26
First, let me say thanks for the help.
I just have the default Intel graphics device, not a GForce, etc.  I do have values like you do.
My monitor is listed, not "Generic Monitor"
And my resolutions are 1024x768  800x600  640x480
But like I said, none of those values are in the screen resolution tab on the desktop.
My Default Depth in the Screen section is 16, not 24 like your example.

---

### Post by Teroedni on 2005-09-26
Ok lets try with an modeline then .Hope this works for you

    
Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802




       Yust write the modeline yust after the vert refresh

Heres an demo of how it should look
    


     Section "Monitor"
     Identifier "dell or whatever you have put in here"
     Option "DPMS"
     HorizSync 28-85
     VertRefresh 43-90
     Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802
EndSection

---

### Post by cdouglas on 2005-09-26
I tried it, but still the same resolution, and no option to change the value.

---

### Post by Teroedni on 2005-09-26
I am running out of ideas:(
Your sure you cannot get the machine on the net ??

I really need to see your xorg.conf to be able to help

---

### Post by cdouglas on 2005-09-26
I just sent you a priate message.
I did get online, but with the resolution so out of whack, it's hard to use.

---

### Post by Teroedni on 2005-09-26
Ok it seems like you have done it right

Intel chipset is not the easiest to configure:(

Can anybody else help as im out of luck:(

---

### Post by cdouglas on 2005-09-26
Thanks for all the help.  You've gone above and beyond the call of duty.

---

### Post by DoeRayMe on 2005-09-26
use this, just change some of the information

> Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel 82845G"
	Monitor		"SyncMaster"
	DefaultDepth	24
        Defaultfbbpp 32
	SubSection "Display"
	Depth		24
        FbBpp 32
	Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by cdouglas on 2005-09-26
That caused an error message upon boot.  Failed to start X server.  Likely no set up correctly.
X server now disabled.  Restart GDM when it's configured correctly.
This kept happening yesterday, so I kept reinstalling the OS.  Is there an easier way to correct the problem without reinstalling?

---

### Post by DoeRayMe on 2005-09-26
It should not, its what i use

Could you post your file please

---

### Post by Teroedni on 2005-09-28
Try with the 810 driver instead 

NAME

i810 - Intel 8xx integrated graphics chipsets
SYNOPSIS

Section Device Identifier devname Driver i810 ... EndSection
DESCRIPTION

i810 is an Xorg driver for Intel integrated graphics chipsets. The driver supports depths 8, 15, 16 and 24. All visual types are supported in depth 8. For the i810/i815 other depths support the TrueColor and DirectColor visuals. For the 830M and later, only the TrueColor visual is supported for depths greater than 8. The driver supports hardware accelerated 3D via the Direct Rendering Infrastructure (DRI), but only in depth 16 for the i810/i815 and depths 16 and 24 for the 830M and later.
SUPPORTED
HARDWARE

i810 supports the i810, i810-DC100, i810e, i815, 830M, 845G, 852GM, 855GM, 865G, 915G and 915GM chipsets.

---

### Post by torstenprahl on 2005-09-28
Hi,

I am having the same problem:

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"DELL M781s"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL M781s"
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


I am very new to the Linux world.  Step by step instrcutions would be greatly appreciated.

Thanks,

T

---

### Post by torstenprahl on 2005-09-29
Well I figured it out with the help of a friend in my office.  :) 

I was mostly affraid of editing my xorg file and was not sure how to do the actual editing.  I didn't realize you just have to literally add the lines into the file and save.

after all said and done here is what my xorg file is:

Section "Monitor"
	Identifier	"DELL M781s"
	HorizSync	31.5-80
	VertRefresh	36.5-75
	Option		"DPMS"
	Modeline "640x480" 25.175 640 664 760 800 480 491 493 525 #60Hz
Modeline "800x600" 40 800 848 968 1056 600 601 605 628 +hsync +vsync
Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"DELL M781s"
	DefaultDepth	16
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

Regards,

Torsten

---

### Post by Vardor on 2005-09-29
Try this:

write at the console

```
gtf 1024 768 60
```
(or the resolution you want), you'll obtain something like this:

```
# 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
Modeline "1024x768_60.00" 64.11 1024 1080 1184 1344 768 769 772 795 -HSync +Vsync
```

Then add this lines to /etc/X11/xorg.conf in the section "monitor" beetwen ***Section "Monitor"*** and ***EndSection***
Finally add this mode (1024x768_60.00) in the section "Screen", subsection "Display" in *Modes* as follows:

SubSection "Display"
Depth 24
Modes "1024x768_60.00" "640x480"
EndSubSection
You can do this for all the modes you want to add.

---

### Post by cousteau on 2007-02-05
---quote---
With a fresh install of Red Hat 9 on a Dell Dimension 4600, the only video mode that would work with XFree86 was 640 x 480, which is ludicrously big on a decent-sized monitor. Changing the config didn't do anything, even though the config was well within my monitor's limits.

The solution was to go into the BIOS setup and change the Integrated Devices (LegacySelect Options) / Onboard Video Buffer setting from 1 MB to 8 MB. I'm not sure what the tradeoff with other aspects of the system is, but X nicely starts up at 1280 x 1024. Apparently, this is the solution for other Dell models as well, including the Optiplex GX260; mine had Dell BIOS Revision A08. Also, it seems to be the case that the problem is general to XFree86, although it manifested for me under Red Hat 9.

Thanks to Erick Tonnel at Dell, who kindly provided the solution.
---quote---

Worked on my machine. Ubuntu started at 1024x768 after this BIOS-change, not bad for a start. After that I reconfigured the XServer via the standard command

sudo dpkg-reconfigure xserver-xorg

and told the machine about the installed Intel-chipset and the features of my monitor, and Ubuntu booted at 1280x1024 at 75 Hz, which is perfect for my Dell 1702FP.

Well, hope this helps ...

---

