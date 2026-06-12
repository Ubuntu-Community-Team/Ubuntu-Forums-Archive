---
title: "Proprietary Drivers"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by x-r4y on 2008-06-26
Hy, well I'm using Ubuntu in GNOME session, and I have a question to the ATI Proprietary Drivers.

When I don't install it graphics during Games kinda suck (no wonder ^^) e.g Alien Arena, Warsow or Sauerbraten. 

The problem though is when I have the proprietary Drivers runny it kinda works and I get an average of 90fps but I get graphical errors like ever half second the Screen looks like its refreshing (although I have 90fps). Wine Configuartion doesn't work at all, and when I go back to the Desktop Environment, it's literally totally screwed, I can't even op the Applications Menu of GNOME cause all the Icons are aligned wrong. 

So I'm asking is it possible to get rid of the Display problems or is it possible to run the Games/Apps without the Proprietary Drivers?

Thx in advance for the Help ;)

[SIZE="3"]**Keep it up Community and make the life of us Newbies easier lol ^^**[/SIZE]

---

### Post by Pumalite on 2008-06-26
Ati does not support Linux the ATI proprietary driver give problems to a lot of people (search the forum). Some people have found happiness with Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by x-r4y on 2008-06-27
Thx for the help ;) Works great ^^

---

### Post by Pumalite on 2008-06-27
You are welcome. Good luck.

---

### Post by sbentjies on 2009-01-06
Every time I tell it to install proprietary drivers, it breaks X. What is going on?

---

### Post by kixome on 2009-01-06
I am using an ATI x300 cheapo card. I used to have the same problem. What I did was install ubuntu, then fully update it, and then install the driver. I also used to experience problems with games when compiz was active, especially with GL games. Hope this helps. If that does not work then try without quotes.  

"sudo aticonfig -- initial" 

#Generates a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.

"sudo aticonfig --resolution=Screen#,W1xH1,W2xH2,W3xH3"

#example:  sudo aticonfig --resolution=Screen0,1280x1024,1024x768"

the first resolution listed will be the default used.
       

" Sets the modes for the specified screen(s).  You may specify several
resolutions separated by commas Screens start at 0.  You can use 1 for dual-head"

GOOD LUCK!

---

### Post by sbentjies on 2009-01-06
Is it safe to assume the same would work for NVIDIA?

---

### Post by sbentjies on 2009-01-06
This is BLOODY amazing....I loaded Ubuntu fresh, told it to use the restricted drivers, and my screen resolution got WORSE. WTF?

---

### Post by sbentjies on 2009-01-07
Back to the core question: Is this considered a glx new, glx or glx proprietary driver? I have the binary installation instructions but must get the right driver. I don't want to flounder about on this. When I do lspci | grep -i nvidia, I get 01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) What does this tell me?

---

### Post by CHaoSlayeR on 2009-01-10
^^ That tells you that you have a rather old card. You will not be able to use the latest nVidia Beta drivers that would fix the performance problems with KDE4 because your card is no longer supported. The latest drivers for your card is the nVidia 177 driver.

If you want 3D acceleration that is your only option. If you can live without it and prefer good speed at desktop usage you should use the xserver-xorg-video-nv driver which is open source.

Setting up displays using the proprietary nVidia driver differs completely from the AMD/ATI approach. It is usually safe to use the GUI tools (nvidia-xconfig or nvidia-xsetting). If that doesn't work you'll have to search the forums for your problem and if you can't find anything just ask for help, always providing your /etc/X11/xorg.conf and /var/log/Xorg.0.log. Then it's most likely that you'll have to manually edit your xorg.conf because drivers sometimes choose wrong modes for displays or screw up other parts of the X.


@kixome:

If you are using an X300 card you can safely use the open source radeon driver. I installed that one on a machine with an X1350 card in dual head configuration and I got full 3D acceleration. Also configuration for those open source drivers is much easier and they seem to just work. Regarding the OpenGL speed there is nothing bad I could say. With glxgears I got around 2400 FPS and all KDE4 effects are working smoothly on that machine. I got full DRI and XVideo acceleration too (tested with some Full-HD material, CPU at 5-10%). So if you don't want to struggle the next time you upgrade try that one instead and you should be fine.


C]-[aoZ

---

### Post by sbentjies on 2009-01-10
This is a free Dell GX-150, ideally suited to run Linux and I'm not gaming so the goal is good video performance but not necessarily 3D acceleration. Again, I'd just settle for a nice resolution, above 800x600. I have had trouble with nvidia-config. Perhaps nvidida-xsetting would work. I assume the object is to just get the X settings right for that card. This has been ridiculously hard.

---

### Post by sbentjies on 2009-01-10
On running nvidia-xconfig I get the error "VALIDATION ERROR: Data incomplete in the file /etc/x11/xorg.conf, Device section "Configured Video Device" must have a driver line.

---

### Post by sbentjies on 2009-01-10
Here is my xorg.conf (for the thousandth time). 

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by CHaoSlayeR on 2009-01-10
Do you have a running posts per month competition or why is it that you can't find the "edit" button?

Sorry for that. But it makes reading easier somehow when the information is bundled in one post.

Regarding your problem with nvidia-xconfig I never had such an issue and you are sure you are running it as root? Your xorg.conf posted here doesn't seem to be the same that nvidia-xconfig is using when you get the "VALIDATION ERROR". Otherwise nvidia does some magic I'm not aware of or do you have another device section with identifier "Configured Video Device" inside the xorg.conf?

As a little reference I post mine here that I have used successfully for some time (although it is a dual head version):
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "LGP"
	HorizSync       30.0 - 75.0
	VertRefresh     60.0
EndSection

Section "Monitor"
	Identifier     "Monitor1"
	VendorName     "Unknown"
	ModelName      "NEC FE1250+"
	HorizSync       30.0 - 110.0
	VertRefresh     50.0 - 160.0
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "TwinView" "0"
	Option         "metamodes" "DFP: 1280x800_60 +0+0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Screen"
	Identifier     "Screen1"
	Device         "Device1"
	Monitor        "Monitor1"
	Option         "TwinView" "0"
	Option         "metamodes" "CRT: 1600x1200_85 +0+0"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "Extensions"
	Option         "Composite" "Disable"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 1600 400
	Screen      1  "Screen1" 0 0
EndSection

Section "Device"
	Identifier     "Device0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce FX Go5200"
	BusID          "PCI:1:0:0"
	Screen          0
	Driver         "nvidia"
        Option         "BackingStore" "true"
EndSection

Section "Device"
	Identifier     "Device1"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce FX Go5200"
	BusID          "PCI:1:0:0"
	Screen          1
	Driver         "nvidia"
        Option         "BackingStore" "true"
EndSection

Section "ServerFlags"
	Option         "Xinerama" "1"
	Option         "AIGLX" "false"
EndSection


```

The panel in my Dell Inspiron 8600 is only 1280x800 but at work there are some folks with a 1920x1050 panel and they all get their desired resolutions, regardless of the driver.

When you want just good video and desktop performance the nv driver may make you happy too. As you are only using one display you don't have to struggle with anything and it should just work out of the box.

C]-[aoZ

---

### Post by sbentjies on 2009-01-10
If I had a cohesive fix for this, my posts would be done. As is, I have no real solutions and an nvidia card that's about to be abandoned. It ceased to be fun weeks ago. Your xorg.conf is very different. My understanding is that with 8.04 and higher, configuring xorg.conf should be a thing of the past. What I need to hone in on is what method and what drivers should I be using? I'm tired of annoying peeps on this board, although thanks all round are deserved for replies.

---

### Post by jrusso2 on 2009-01-10
> **x-r4y said:**
> Hy, well I'm using Ubuntu in GNOME session, and I have a question to the ATI Proprietary Drivers.

When I don't install it graphics during Games kinda suck (no wonder ^^) e.g Alien Arena, Warsow or Sauerbraten. 

The problem though is when I have the proprietary Drivers runny it kinda works and I get an average of 90fps but I get graphical errors like ever half second the Screen looks like its refreshing (although I have 90fps). Wine Configuartion doesn't work at all, and when I go back to the Desktop Environment, it's literally totally screwed, I can't even op the Applications Menu of GNOME cause all the Icons are aligned wrong. 

So I'm asking is it possible to get rid of the Display problems or is it possible to run the Games/Apps without the Proprietary Drivers?

Thx in advance for the Help ;)

[SIZE="3"]**Keep it up Community and make the life of us Newbies easier lol ^^**[/SIZE]

90 FPS is too slow for modern 3d games.  My card does 4000 FPS and is really not fast enough for the best games.

I have Nvidia 9600 GS on this with 512 mh of ram

---

### Post by sbentjies on 2009-01-10
Where the community can step in is say "hey newb, use NV with that FX-5200-Nvidia doesn't support it, or use nvidia drivers 177.xx.xx . I have done everything except compile a kernel for it and being a noob would not feel comfortable with that. That and who would want my monolithic kernel? There has got to be a "preferred" way to do this amongst the community. If I need to re-post any info I will. I'm flailing about in the dark here.

---

### Post by CHaoSlayeR on 2009-01-10
> **sbentjies said:**
> Every time I tell it to install proprietary drivers, it breaks X. What is going on?

Well, why do you want to use the proprietary driver if you don't need 3D acceleration? Why do you think those guys over at nvidia are better linux driver developers than the folks over at X.org? That's like making an electrician responsible for the mistakes of the architect. And right now you are complaining about that at the neighbor.

Go to nVidia and file a big bug there! Ranting here won't help you out regarding your proprietary driver problem.

If you did a fresh install the system already should pick the right driver for you (of course not one of the binary blobs). Only if something doesn't work at all but that you need that feature you should consider using a non open source driver. But that doesn't seem to be the case:

> **sbentjies said:**
> This is a free Dell GX-150, ideally suited to run Linux and I'm not gaming so the goal is good video performance but not necessarily 3D acceleration. ...

In addition if have posted more specific information in another post please link it here so people have the chance to get the information about the system they need. Ranting around won't help you, in the worst case it'll do the exact opposite.

I did a search and linking your specific problem here as others may have that issue too: [http://ubuntuforums.org/showthread.php?t=1033046](http://ubuntuforums.org/showthread.php?t=1033046)

I will reply to that topic from now on to your problem.

C]-[aoZ

---

### Post by sbentjies on 2009-01-10
I'm not trying to rant, just a little frustrated. When I enable the proprietary drivers it gets worse-I only get 640 x 480. None of the nvidia drivers work. If I knew what approach to take, I'd take a run at it. I've broken X more times than I can count. One thing of note, the system is not "seeing" the card, registering as "unkwown". Oh, and I tried the Envy drivers in the Universe and Multiverse repositories. No go-X breaks. :(

---

### Post by sbentjies on 2009-01-10
It would appear that my card is not the only Nvidia card to give such problems:

[http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a.html](http://www.linuxforums.org/forum/ubuntu-help/120492-nvidia-driver-problem-very-weird-ubuntu-8-04-a.html)

---

