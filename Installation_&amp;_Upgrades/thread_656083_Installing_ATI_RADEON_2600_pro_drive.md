---
title: "Installing ATI RADEON 2600 pro drive"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by ster1988 on 2008-01-02
I just installed ubuntu today. I have never used linux before so i am kind of lost here. I have found the right .run file for what i need. However when i double click on the file i just get an"Couldn't display "/home/sterling/Desktop/ati-d...ler-8.443.1-x86.x86_64(2).run". i am starting to get nauseous because my computer can only be at 800X600 so how exactly do i go about installing this, is there any videos or through instructions. Again i have _never_ used linux before. I was tryign to mess around witht the terminal screen but i dont really know whats goign on. I managed to dual boot xp along with this but i would like to learn more. Any help is appreciated. 

Thank you.

---

### Post by Ub1476 on 2008-01-02
You have two ways to do it. The ubuntu way, or the manual way. The driver which is in Restricted Driver Manager is not the latest driver though (due to stability). [Here's a good guide for both.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way") I suggest doing some googling to see what drivers work best for your card.

---

### Post by ster1988 on 2008-01-02
ok on that guide i got as far as running this command 
root@sterling-desktop:~# bash ati-driver-installer-8.443.1-x86.x86_64.run --buildpkg Ubuntu/guts
bash: ati-driver-installer-8.443.1-x86.x86_64.run: No such file or directory
root@sterling-desktop:~# 
then i get that no such file or directory exists, what should i do ?

---

### Post by Ub1476 on 2008-01-02
You can use [Envy]("http://albertomilone.com/nvidia_scripts1.html").

After it's installed, launch it by:

```
envy -g
```

It will grab the latest driver for you, install them and configure them.

---

### Post by ster1988 on 2008-01-02
i downloaded envy, and now after rebooting after their installation my monitor wont display anything? why is that ? how do i fix it.

---

### Post by ster1988 on 2008-01-02
should i just re install ubuntu it seems to have a lot of problems

---

### Post by 2600 2560x1600 on 2008-01-12
I downloaded & installed envy. After running it, fglrx driver successfully installed. I was able to run in 2048x1536 instead of 1920x1440.

But, my monitor is 2560x1600. Does anyone know whether it is possible to run in 2560x1600 on ubuntu with ATI?

thanks!

---

### Post by StigOE on 2008-01-22
I'm also trying to install an ATI HD2600 PRO in Ubuntu 7.10, but whenever "fglrx" is enabled and I reboot, I loose the picture on my screen. It looks kind of like it reboots in a loop because the resolution is wrong. The screen is a ViewSonic VG800. Can anyone tell me where the supported resolutions for each screen are stored, so I can try to edit out the resolutions that are too high?

If I start "Restricted Drivers Manager", I get the message "Your hardware does not need any restricted driver". I've tried to install the driver manually and using Envy, but everytime I reboot to use the driver, I loose the picture.

Thanks in advance.

Stig

---

### Post by StigOE on 2008-01-23
Replying to my own post here... :-)

I've tried to fiddle some more with this, but still no luck. I've tried to add modelines for my monitor, but whatever I do, as soon as I enable "fglrx" and reboot, I loose the picture on the screen.

Here's the relevant parts of my xorg.conf. Does anyone see anything obviously wrong?

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"vesa"
#	Driver		"fglrx"
	BusID		"PCI:1:0:0"
#	Option		"VideoOverlay"	"on"
#	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"VG800-2"
#	Option		"DPMS"
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
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"VG800-2"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"EETI"	"SendCoreEvents"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

---

### Post by bwtranch on 2008-01-23
The driver is commented out for one. I don't even know if you have the right driver installed for another. I have no output of the logs. Working in a vacuum. Maybe you should read up on the how-to s.

---

### Post by StigOE on 2008-01-23
Hi and thanks for the answer.

I know the driver is commented out. Otherwise my monitor would have blanked out. And I have read several how-to on how to install the driver, but no matter what I do, when I enable the fglrx-driver, the monitor craps out... I have tried to install the latest driver from ATI, both manually and using Envy.

Which logs would you like to see?

Stig

---

### Post by jmbenson89 on 2008-01-23
I'm having the same problem with my ATI Radeon 2600 Pro.  

-I have tried going to Restricted Drivers and enabling it in there.  On reboot, the screen is completely black and I have to restart to do anything. 
-I tried using Envy to install the ATI drivers, and on reboot it worked, but everything was extremely choppy: moving windows, scrolling, etc.  So I took that off.
-I tried this: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) but it failed, as I mentioned in this post: [http://ubuntuforums.org/showthread.php?t=675708&highlight=ati+radeon+2600](http://ubuntuforums.org/showthread.php?t=675708&highlight=ati+radeon+2600)

I have to change my driver in the xorg.conf file to "vesa" for it to work, but then I only get 2D support.  Has anyone at all made this exact graphics card work?

---

### Post by Von on 2008-02-07
Just wanted to put my $0.02 in on this discussion.   I have a Shuttle machine with an  onboard nvidia 6100 that I had been using and then I installed an ATI Radeon 2600 pro.   For the longest time I would switch between both PCIe ATI, and onboard nvidia,  when I switched between XP and Ubuntu 7.10.  

I used the second method[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually") and rebooted numerous times and  after running through the steps my system would still not recognize the ATI card whenever i ran fglrxinfo it would not show any sign of ATI.  After running the package install command [COLOR="DeepSkyBlue"]sudo sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy[/COLOR] again and rebooting it worked like a charm. 

I am very new at this sorry for the lack of details.

---

