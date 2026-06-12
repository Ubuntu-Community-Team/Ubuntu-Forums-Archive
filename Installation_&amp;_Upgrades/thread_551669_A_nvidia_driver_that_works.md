---
title: "A nvidia driver that works?"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by dutch_boi1 on 2007-09-15
hey i have had my ubuntu working fine for many times its just witht he newest ubuntu ive seem to run into a brickwall.. 3 times.

I tried installing the drivers through envy and all i got was no display
i tried installing the drivers from nvidia's website, wouldnt let me.
i tried installing the drivers from the restricted area, no display.

How can i install my drivers? when i look through my xorg.conf and find the sectiion about display and i change the driver to nvidia and next reboot the screen blanks. The only drivers that seem to work are "nv" and Vesa.

So how can i get my nvidia product working?

---

### Post by Pumalite on 2007-09-15
Are you talking about Gutsy?

---

### Post by dutch_boi1 on 2007-09-15
hey 7.04 ?

---

### Post by Pumalite on 2007-09-15
7.04 should be no problem. Can you explain this a little more extensively:
'i tried installing the drivers from nvidia's website, wouldnt let me'.

---

### Post by t3hi3x on 2007-09-15
What video card do you have?

ex 8800gts?

Is it a laptop video card?

---

### Post by dutch_boi1 on 2007-09-15
hey sorry about the short info i was in a rush as i had to go. In my system i have a nvidia 7950GT 512mb.. so i searched the forums on how to install the driver. As stated earlier i ran into a brickwall with all 3 tries.

The first thing i tried was envy, it downloaded fine andit run fine as thats what it said anyway. So i launched envy and clicked install nvidia drivers and it was doing its thing, by the time i knew it,it had finished. SO i rebooted to only get a black screen (blue on mine, same as no signal) but i could hear eveyrhting loading. So i ctrl+alt+F1 into another space in asence, logged in and sudo'd to my xorg.conf. I searched through it about 3-4 times for anything out of place. I didnt find a problem with my device's section.

As i have no display to work of, ima use a rough idea of how it went.
The driver pointed to nvidia, it had airgbextensions as true? (not sure in exact name, the ones for compositing etc) and then it had all my resolutions etc along with device names.

So after that i changed the nvidia into a nv and rebooted. It worked but i was stuck with the lowest resolutions even after modding my xorg.conf. So i tried using my original backup and went sudo nvidia-xconfig. It said it made a new xorg.conf but still no success.

What i meant with the driver of their site is that even though i tried to close the xserver, (invoke-rc gdm stop) from the instructions of nvidia's site it kept telling unkwon command, invoke-rc. So i couldnt even launch the installer.

Im jus tthinking, whats the best way to install the nvidia drivers, in 4.x and 5.x  it used to be really quite simple =\.

Anyone care to point me in a good direction?

---

### Post by Pumalite on 2007-09-15
Try: sudo /etc/init.d/gdm stop
sudo sh /path/to/the/driver/NVIDIA-Linux-x86 blah, blah, blah
Accept license, let driver remove old drivers and compile module, let driver reconfigure your xorg file
sudo /etc/init.d/gdm start
If need be: startx
Make sure you have build-essential:
sudo apt-get build-essential

---

### Post by dutch_boi1 on 2007-09-16
Hey ok i did as u said, installed the nvidia driver, it compiled the kernel, installed the driver but when it came to starting GDM i just got a blue screen which means no signal. atm im in ubuntu with the driver running @ NV not nvidia.

I thought it would be best to post a segment of my xorg.conf file. well here it is:

Section "Device"
	Identifier	"Nvidia 7950GT"
	Driver		"nv"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia 7950GT"
	Monitor		"ViewSonic"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection




Is there anything that i need to change? because if i use the nvidia driver all i see/hear is the login sounds when hte login manager loads, but i dont see anything.
edit: i changed my monitor in there, but i changed all the other required fields, i can change it back if u wish

---

### Post by dutch_boi1 on 2007-09-16
ok its official. The nvidia driver does not like me. When i change it to nvidia it doesnt work, when it is vesa or nv it does. I dont know why :( am i meant to like have a busID or something in there? i know when i tried hackintosh i had to change my device ID's.

---

### Post by dutch_boi1 on 2007-09-16
Well i have found no solution, ive noticed that none of my other distro's will load on my machine :O. Freespire, Suse, ubuntu 6.10 or debian. They all cry about the cd not being mounted. Could it be within my motherboard? the P35 chipset or my Q6600 cpu? i mean i would assume these are all supported yes?

---

### Post by Pumalite on 2007-09-16
I think the Nvidia 7950GT is not supported.

---

### Post by dutch_boi1 on 2007-09-16
hey yeah well thats very odd as ive used this exact same card with my old machine (AMD athlon 64 4200+) and it worked fine.

Weird

---

### Post by t3hi3x on 2007-09-18
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

this is a list of all the supported drivers as of the latest nvidia linux drivers:

> ...

GeForce 7900 GT/GTO 0x0291 
GeForce 7900 GTX 0x0290 
GeForce 7950 GT 0x0295 
GeForce 7950 GX2 0x0294 
GeForce 7950 GX2 0x0293 
GeForce 8300 GS 0x0423 
GeForce 8400 GS 0x0422 

...

Have you tried installing it via envy? i have always had great luck with that application.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

let me know if that works or not.

---

