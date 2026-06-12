---
title: "Upgrading to Gusty - a few problems :("
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Znupi on 2007-11-13
Hello,

I had Feisty before, and it worked perfectly. Then I wiped it (formatted its partition) and installed Gusty. Now I have some problems (in order of importance):

1) Restricted drivers for my ATI Radeon X550 Video Card (512MB RAM) don't work -- although they worked on Feisty. This is very strange, when I install them and reboot, before the login screen, the screen flickers a few times and then Ubuntu goes into "low-graphics" mode. Could it be because I changed my screen type (under System -> Administration -> Screens and Graphics or something like that, I can't tell now because I'm on Windows 8-[)? I changed it because I couldn't get 75Hz and I set it to "LCD Panel 1280x1024" because so far it's the only one that's working -- I don't know what it was set to before I changed it and if I click "Detect" it selects "Plug & Play" which has a maximum resolution of 800x600. Because of this problem some Compiz Fusion effects don't work properly (I'm using Compiz Fusion without Xgl because with Xgl nothing really works -- everything is painfulllly slow). Has this happened to anyone before? Is there a solution / workaround?

2) In /boot/grub/menu.lst I changed "default" to "saved" just like I did on Feisty, but now it only boots Windows :???:

3) As stated in 1) -- I can't get 1280x1024 @ 75Hz although my display is capable of it. My display is a Philips 170S2 and it isn't listed under "Philips" in Screens and Graphics.

Thank you for reading my post and thank you for any help :)

---

### Post by Triptol on 2007-11-13
1&3) I had some bad experiences using the control panel thing with setting X. For me it always worked better by setting the driver to fglrx in the xorg.conf (Driver "fglrx"). Setting it to fglrx will use the ATI proprietary driver. If you want to use the open source driver you could go with "radeon" or even "ati" IIRC.

2) you also have to add a line "savedefault" (no quotes) to each entry that you want to be saved.

---

### Post by Znupi on 2007-11-14
Ok so I ran
```
sudo apt-get install xorg-driver-fglrx
```
and then changed Driver to "fglrx" in xorg.conf and the "low-graphics" thing happened. If I leave it set to "ati" and type fglrxinfo, here's what I get:
```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1

```
And attached is my xorg.conf file. Please help :( Thanks :)

---

### Post by Znupi on 2007-11-15
Anyone? :(

I'm thinking of reinstalling Feisty (on Feisty the drivers worked with no problem), installing the restricted drivers on it, backing up the xorg.conf on another partition, installing Gusty again, installing the drivers and replacing xorg.conf with the one from Feisty. Would that make any sense? Do I have a chance to get it working like that? It would only take me like an hour probably because Ubuntu installs sooo faaast :)

Thanks :)

---

### Post by mamlouk on 2007-11-15
I have an ATI X550, and I've had a bad experience installing the ATI driver and I had to roll back to the Linux open-source driver. However, I decided to research before trying it again, and it seems that you're into the MESA dilemma. Have a look at [that]("http://combatwombat.7doves.com/index.php/2007/10/31/gutsy_effort_in_new_ati_driver"), it might help you with the MESA thing.

Tell is if it works.

---

### Post by Triptol on 2007-11-15
Well judging from your xorg.conf you still are using the ati driver:
```
Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:2:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
```
Driver says "ati" here, so you should change that to fglrx. Remember to edit it with sudo (using the root account) or else changes will not be possible.

If things don't work you will find more info in the file /var/log/Xorg.0.log. 

Good luck!

---

### Post by soxs on 2007-11-17
If you don't have dual monitor setup, I would say the whole xorg.conf is corrupted.
I guess you used the gtk interface to identify your monitor/grphicscard? I allready filed a bug report for that app. It sily screws up the whole xorg.conf. I will attach a "cleaned" version (make a backup before you use this one, it might fail, although it shouldn't)
Note: The xorg.conf only works correctly with the latest ATI driver EXCLUSIVLY!
Btw.. I have a R300 NE ^^ and it works fine...

---

### Post by mamlouk on 2007-11-20
Done it tonite on my 2.6.22-14-generic kernel using the instructions on [this site](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide). I'm using an Ubuntu 64 edition, with my ATI X550. Got my Desktop Effects working now, and I feel good.

Next step is to get it up on my 2.6.23 kernel.

---

