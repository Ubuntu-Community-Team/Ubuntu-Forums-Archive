---
title: "Update to kernel 2.6.24-17-386 messed up graphics"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by ahood on 2008-05-26
Need help...

I am running Ubuntu Hardy Heron (8.04) and all was well until I clicked on the Update Notification icon in the task bar and applied/installed all the updates, which included a new kernel 2.6.24-17. After the update finished, I rebooted as instructed. However, I was greeted with low graphics mode (vesa) despite having an NVIDIA 7800 GS (AGP) graphics card and drivers installed.

Reinstalling the nvidia-glx-new drivers didn't solve the problem. I have tried installing drivers downloaded from NVIDIA website, but it won't install. The script keeps complaining that an xserver is running even though I used the ctl+alt+f1 prior to installing the proprietary driver.

I ran the "Screen and Graphics" utility with the nvidia-glx-new and selected NVIDIA from the list, but the Available Driver option (opensource versus proprietary) is greyed out.

If I click on System --> Administration --> Hardware Drivers, the white area is completely empty.

I have tried uninstalling nvidia-glx-new and installed nvidia-glx-new-envy, but the problem persists.

WARNING RANT: :mad: I am very frustrated with Ubuntu Hardy and this has been the worst experience with an Ubuntu release yet (Feisty was great!). I wish this was easy!!!!!! Okay, I got that off my chest. 

If anyone can suggest a solution, I will be most grateful. I will continue to search this forum for a solution, and if found, I will post back.

---

### Post by Pumalite on 2008-05-26
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop (to stop the xserver)

---

### Post by CryNoz on 2008-05-26
> **ahood said:**
> Need help...

I am running Ubuntu Hardy Heron (8.04) and all was well until I clicked on the Update Notification icon in the task bar and applied/installed all the updates, which included a new kernel 2.6.24-17. After the update finished, I rebooted as instructed. However, I was greeted with low graphics mode (vesa) despite having an NVIDIA 7800 GS (AGP) graphics card and drivers installed.



Woke up this morning and did the same thing :/

But I found this to work. 

1. Go to synaptic and search for "restricted"

2. Install **linux-restricted-modules-2.6.24-17-generic**

3. Remove [B]linux-restricted-modules-2.6.24-16-generic
[/B]
4. Restart

Nvidia should be back up and running :guitar:

---

### Post by nugznmugz on 2008-05-27
I am having the exact same issues.  I also have a Geforce 7800 GS AGP.  It appears that once the nvidia-glx-new package is installed my video settings go crazy.  I can't get the resolution above 800x600 and cant control the refresh rate either.  The strange part is that all of the compiz-fusion options work.

I have the nvidi-settings package and it recognizes my card when the driver is enabled, but my display is not detected correctly.

I'll be keeping my eye on this thread as I'm sure its an issue with my video card...

---

### Post by wzf851005 on 2008-05-27
These patterns are based on different foot type, weight, Speed, training programmes, gender and skill level design. These different styles, different prices and multi-purpose products, attracting hundreds of thousands of jogging, making them feel that [nike shoes](http://www.bestbuynike.com) is to provide the most complete variety of running shoes manufacturers, millions of range of ability Running to have that belief.   First-generation jordan shoes uppers, there is a conspicuous "Chachi basketball" signs in the use of trapeze signs ago, the first generation and second generation Chachi Jordan basketball shoes are used as signs. First-generation[jordan shoes](http://www.pickyourjordan.com) appeared in 1985, 1994 and 2001 NIKE companies produced twice again this shoes. For the classic colors with a red, black, and compared with black. [Air Jordans](http://www.oknike.com), published in 1991, jordan shoes91-92 season Zhanxue because jordan shoesin the Barcelona Olympic Games 92 wearing this pair of 7 and winning the title, the seventh generation in jordan shoesin the series, it is particularly valuable. 7 and the shape of the shadow of some six generations, the biggest feature is particularly color.  Borrow a relatives [chinese dress](http://www.prettyladygirl.com/). Sometimes those old chinese dresses are outdated beyond repair, but then again, sometimes theyre not. If you have an (aunt, mom, cousin, sister) who got married in a strapless sheath that would be perfect, theres no reason you couldnt too, assuming theyre open to loaning it out. You can still make the look your own with the veil, jewelry, shoes, a pretty sash. And youll have that &#8220;something borrowed&#8221; checked off the list.What about the modern cheongsam? With more exchange with the outside world, todays [cheongsam](http://www.prettyladygirl.com/) combines both Chinese and western characteristics, traditional and modern features. There are bold changes and innovations. Whatever it is, cheongsam on one hand can still create an impression of simple and quite charm, elegance and neatness. On the other hand, blended with modern features, they can also show peoples individuality and distinctiveness. No wonder cheongsam enjoys a growing popularity in the international world of high fashion.

---

### Post by ahood on 2008-05-27
> **Pumalite said:**
> Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop (to stop the xserver)

Thank you for this tip Pumalite!

I did get past the error message described above and proceeded to give me another error message.

This second error message is a complaint about kernel-source not being installed.

I searched the Synaptic Repository and found linux-source and installed this package. 

Unfortunately, this second error message persists, presumably because the kernel-source that the NVIDIA installation script seeks isn't found.

I do appreciate the help and suggestion. :)

---

### Post by ahood on 2008-05-27
> **CryNoz said:**
> Woke up this morning and did the same thing :/

But I found this to work. 

1. Go to synaptic and search for "restricted"

2. Install **linux-restricted-modules-2.6.24-17-generic**

3. Remove [B]linux-restricted-modules-2.6.24-16-generic
[/B]
4. Restart

Nvidia should be back up and running :guitar:


Thanks for the suggestion CryNoz! :)

I really had nopes that this would work. Unfortunately, the situation hasn't changed. I am still hopeful though. I am wondering whether there is still a package missing that is needed and that I uninstalled by mistake.

When I get home tonight, I will review all the recommended packages necessary for the nvidia-glx-new driver and make sure nothing is missing.

If anyone can post an additional suggestion on a possible solution, I would be very grateful.

---

### Post by kuyote on 2008-05-27
Unfortunately this didn't work for me either.

I'm assuming that when you said to install this, linux-restricted-modules-2.6.24-17-generic, it actually corresponds to the kernel you have installed. I used the linux-restricted-modules-2.6.24-17-server, since I have the server kernel installed.

---

### Post by kuyote on 2008-05-27
So after installing nvidia-new-kernel-source, it looks like I have something promising. I had to clear out my xorg.conf, and re-run the nvidia-xconfig, but now I'm back up and running.

---

### Post by Pumalite on 2008-05-27
> **ahood said:**
> Thank you for this tip Pumalite!

I did get past the error message described above and proceeded to give me another error message.

This second error message is a complaint about kernel-source not being installed.

I searched the Synaptic Repository and found linux-source and installed this package. 

Unfortunately, this second error message persists, presumably because the kernel-source that the NVIDIA installation script seeks isn't found.

I do appreciate the help and suggestion. :)

sudo apt-get install build-essential

---

### Post by maraja on 2008-05-27
I was about to give up after having tried this clues, tried envy and went nowhere.

At the end the solution for me was to uninstall everything related to nvidia, then reboot.
Then I got the installer from nvidia ([http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)), stopped gdm, reinstalled the driver and finally get my Fx5200 up'n'running again...

Wondering one day in the future to have apt-get do the work for me (just moved to VirtualBox to avoid recompiling vmware everytime the kernel changes).

Loong life to Ubuntu!

---

### Post by ahood on 2008-05-31
Thank you to kuyote, CryNoz, Pumalite, nugznmugz, and maraja!

The quick replies and many suggestions are much appreciated.

My experience has been interesting to say the least. I did solve the problem described above, but I used yet a different solution.

Nothing I did would break the link between kernel 2.6.24-17-386 and vesa graphics mode. I attribute the unbreakable link to either a very strong love affair between this particular kernel and vega or to an equally strong hatred between this particular kernel and nvidia-glx-new. The strength of the passion between these was admirable.

However, I wanted my 1440x900 resolution back and nvidia powered desktop back!

The solution I was forced to do was to uninstall the following packages

> linux-restricted-modules-2.6.24-17-386
linux-ubuntu-modules-2.6.24-17-386

I then installed, or verified,that the following packages were installed

> linux-restricted-modules-2.6.24-16-386
linux-ubuntu-modules-2.6.24-16-386
nvidia-glx-new
nvidia-kernel-common


I then rebooted and wonderfully, I was NOT notified that I was in low-graphics mode and the system was going to use the vesa driver. Hurray!!!!

However, I was still in a very low resolution (640x480). So, I clicked on Settings --> Administration --> Hardware Drivers and I was very pleased to see 'NVIDIA accelerated graphics driver (latest cards)' appeared, although the checkbox was empty.

So, I checked the checkbox next to the NVIDIA option, closed the Hardware Drivers window, and logged out/back in.

Upon logging back in, I was still in low resolution mode (640x480). I attempted to change the resolution by clicking on System --> Preferences --> Screen Resolution.

Unfortunately, I was greeted with the following message.

> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

I searched the ubuntuforums and found a few posts that addressed the XRandR issue, which involved manually editing the /etc/X11/xorg.conf file.

So, I executed the following command in a terminal.

> sudo nano /etc/X11/xorg.conf

The output was the following:

> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1440	900
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "ServerFlags"
EndSection


I manually edited the xorg.config file (see below)
> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "[COLOR="Red"]1440x900@50[/COLOR]" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1440	900
		Modes		"[COLOR="Red"]1400x900@50[/COLOR]"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "device" #  
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	1
	[COLOR="Red"]Option "RandRRotation"	"on"
	Option "RandR"	"on"[/COLOR]
EndSection

Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection

Section "monitor" #  
	Identifier	"monitor1"
	Gamma	1.0
EndSection

Section "ServerFlags"
EndSection

I then rebooted the machine and made sure I was booting into linux kernel 2.6.24-16-386.

**SUCCESS!!!!**

After logging into the system, I was running at 1400x900 resolution with the NVIDIA driver in use!

My only wish is that I don't have to do this again; however, because I manually edited the xorg.config file, I suspect that I will have to repeat manually editing this file in order to have an easier time of using the NVIDIA driver if I choose to move to Ibex via an upgrade.

In other words, re-installing Hardy or Ibex from scratch will probably eliminate the need for manually editing the xorg.config file.

I have no plans to move to the 2.6.24-17-386. I don't know if the difficulty I experienced with this newer kernel is specific to my machine or if there truly is a compatibility issue with the NVIDIA driver. I suspect that the issue is specific to my machine.

I hope this thread was useful to others. I learned a lot from my fellow ubuntu users.

Thanks to all.

Al

---

### Post by Pumalite on 2008-05-31
Cheers. Back it up right away.

---

