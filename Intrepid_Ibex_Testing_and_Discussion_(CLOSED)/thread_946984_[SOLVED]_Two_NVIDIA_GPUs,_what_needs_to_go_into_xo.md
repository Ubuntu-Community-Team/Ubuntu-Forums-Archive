---
title: "[SOLVED] Two NVIDIA GPUs, what needs to go into xorg.conf?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klamari on 2008-10-13
Hello

I have been trying to set up Intrepid on my Desktop for days now and do not get past the installation of the NVIDIA 177 driver.

It installs fine, runs under nv with no problems, after installing the new 177 driver after reboot I get a blank screen with a blinking cursor, no reaction on any input. I am able to use TTY 1-6 though. Tried lots of variations to install, no chance....

I guess now that the problem is that there are two GPUs (GeForce 7600GS and 6150) in this machine. My previous experience is mainly SUSE and OpenSuse and using a laptop to install. With Hardy there was no problem to get it running (I am using only one screen so far, never tried to put up a second yet).

I will give you some (I think) relevant specs:

> martin@tux:~$ lspci
02:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 430 (rev a2)

Sorry, I am on Hardy now, don,t know how to copy and paste from TTY:

> dkms status
nvidia, 177.80, 2.6.27-6-generic, x86_64: installed

> xorg.conf

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VenorName      "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    Options        "PixmapCacheSize" "2000000"
    Options        "AllowSHMPixmaps" "0"
EndSection

In my setup I followed this advice: [http://ubuntuforums.org/showthread.php?t=945557](http://ubuntuforums.org/showthread.php?t=945557) 

Running > dmesg doesn't show any obvious errors.

Since the xorg.config does not seem to be as important anymore as in the old days, when I was young I am wondering what might need to go in there in addition to get Intrepid running, I guess the two cards create some confusion either in the driver or in the kernel/system setup.

Something like one 
> Section "Device0" 
Identifier "Video0"

and another with 
> Section "Device1" 
Identifier "Video2"
and defining the PCI numbers?

As an example for a running system I also attach the xorg.conf as created by nvidia.conf in Hardy with 173.13.12 on my machine:
> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    SubSection     "Display"
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection


After all I have read so far about the Ibex when confronted with certain NVIDIA video cards I wonder what people will think about me giving the poor Ibex two opponents, maybe a Ram (RAM 2GB) with its horns can help poor Ibex?

Greetings 

martin

---

### Post by autocrosser on 2008-10-13
I run a SLI system & had to define the main card by bus id#--I would try that first.
The BusID# goes into the "Device" section.
My xorg.conf looks like:

#Custom Xorg

Section "Screen"
    Identifier    "Screen0"
    Device        "Videocard0"
    Monitor        "Monitor0"
        Option          "AllowSHMPixmaps" "0"
        Option          "PixmapCacheSize" "2000000"
    SubSection "Display"
    Depth    24
        Modes    "1920x1200_60"    "1680x1050_60"    "1600x1200_60"    "1440x900_60"    "1280x1024_75"    "1280x1024_60"    "1024x768_75"    "1024x768_60"
    EndSubSection
EndSection

Section "Device"
    Identifier    "Videocard0"
    Driver        "nvidia"
    Vendorname    "NVIDIA Corporation"
    Boardname    "GeForce 8600 GT"
        Option        "Coolbits"    "1"
        Option        "TripleBuffer"    "True"
    Option        "NoLogo"    "False"
    Option        "SLI"    "SFR"
    BusID            "3:0:0"
EndSection

Section "ServerLayout"
    Identifier    "Single-Monitor"
        Screen          "Screen0"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Displaysize    593.28    370.8
    Identifier    "Monitor0"
    Vendorname    "HannsG"
    Modelname    "HG-281DPB"
    Horizsync    24.0-80.0
    Vertrefresh    56.0-75.0
    Option        "DPMS"    "true"
EndSection

---

### Post by klamari on 2008-10-13
autocrosser:

looks like what I had in mind, just was not sure whether those definitions are still read in the xorg.conf as a lot of people keep saying in other threads to use a rather basic one works best (but they refer to single GPUs). 

What puzzles me is that in Hardy the also quite basic file without definitions works well and with Intrepid I cannot get into the GUI at all????? 

Will try to set up definitions and see whether this does the trick (which I hope it does) or whether there is another reason I cannot boot into the graphical system.

Thanks for sharing

---

### Post by autocrosser on 2008-10-14
I've been running Intrepid from almost day one & that xorg.conf is as simple as I can make it with my equipment----Without the BusId, my system wouldn't work......

---

### Post by plun on 2008-10-14
> **autocrosser said:**
> I've been running Intrepid from almost day one & that xorg.conf is as simple as I can make it with my equipment----Without the BusId, my system wouldn't work......

I read manuals....(sometimes) ):P

Is latest correct according to a multi GPU PC ?

[http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-25.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/chapter-25.html)

---

### Post by autocrosser on 2008-10-14
Hummm--I've read that one several times--His problem is that he is running two cards non-SLI & Multi-GPU refers to more that one GPU on the same card....

Quote:
       "The distinction between SLI and Multi-GPU is straightforward. SLI is used to leverage the processing power of GPUs across two or more graphics cards, while Multi-GPU is used to leverage the processing power of two GPUs colocated on the same graphics card."

I'm sure you've pointed him the right way though---just needs to read about how to set-up two cards non-SLI.......

---

### Post by klamari on 2008-10-14
Well, thanks for the reference to Nvidia. :-), havn't tried yet to work on it but looks now I am on the right track.

But:
I thought a major point in the Ubuntu community is to get a simple to install and use system for the unexperienced. So if one has to tweak around in their xorg.conf just to get to access the GUI after install what will the average user do?

- switch to TTY 1, open xorg.conf with > sudo nano /etc/X11/xorg.conf, put in the right settings, type > sudo shutdown -r now ????????

- or hit the power button on the PC, restart with the default pre-installed OS and enjoy a product out of Redmond ???????

My box is not a special setup, bought as is in a retail store, so there will be more of these out there.

---

### Post by klamari on 2008-10-27
Hello, problem solved!!!!:guitar:

I thought I'd give it another go, installed the RC version of 8.10 Kubuntu and guess what, all the same probs again. The solution was to change the xorg.conf similar as stated above. Everything working fine now.

Still, installation is not straightforward and new users will have probs to run 8.10. 8.04 installation on the same system was no prob at all.

Here the xorg.conf that works with one card, havn't tried yet to get both cards running, I am happy to have one working after a lot of trials:)
> Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	BusID		"2:0:0"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Monitor		"Monitor0"
	Device		"Videocard0"
	Option		"AllowSHMPixmaps" "0"
	Option		"PixmapCachesize" "2000000"
	DefaultDepth	24
EndSection


Greetings

martin

---

