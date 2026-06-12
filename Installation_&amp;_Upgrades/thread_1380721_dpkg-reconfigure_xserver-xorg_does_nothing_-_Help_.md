---
title: "dpkg-reconfigure xserver-xorg does nothing - Help please"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by JPKowal on 2010-01-14
I need a video driver for SIS M760GX for an ACER Aspire 5000 laptop.

Everywhere I've looked it says to run 

sudo dpkg-reconfigure xserver-xorg

Supposedly, this is supposed to open a window where I can change settings. However it does nothing and just returns me to the prompt.

---

### Post by dstew on 2010-01-14
What Ubuntu version do you have installed?

---

### Post by JPKowal on 2010-01-14
I had 9.10 2.6.28-11  I didn't work on that one

Now I have 9.10 2.6.31-16  And it still does not work.


Help please. I can't use Ubuntu w/o fixing my video problem. It's usable, but the flickering screen and like 16 colors gives me migraines to look at.

---

### Post by dstew on 2010-01-15
I assume you have looked in System --> Administration --> Hardware Drivers to see if there is a third party driver for your display adapter. And, I assume you have tried the System --> Preferences --> Display panel to fix your resolution. Post to the forum the output of```
lspci
sudo lshw -C display
cat /etc/X11/xorg.conf
```

---

### Post by JPKowal on 2010-01-17
In Hardware Drivers there is nothing except a Wi-Fi driver showing. Display preferences, the monitor is not detected. I can't change anything except the resolution which does not help. I still have like 16 colors, there are weird vertical lines, and what looks like snow or some kind of interference on the display.

lspci:

james@Convict:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

ames@Convict:~$ sudo lshw -C display
[sudo] password for james: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
       resources: memory:e8000000-efffffff(prefetchable) memory:e2100000-e211ffff ioport:a000(size=128)


james@Convict:~$ cat /etc/X11/Xorg.conf
cat: /etc/X11/Xorg.conf: No such file or directory

---

### Post by dstew on 2010-01-17
The video adapter is listed as "unclaimed", meaning there is no specific driver for it. Therefore, it will be used in plain VGA mode, with low resolution. I think the driver is named "sis". The Ubuntu package for 9.10 is named [xserver-xorg-video-sis]("http://packages.ubuntu.com/karmic/xserver-xorg-video-sis"), and can be installed using Synaptic package manager.

By the way, to see the xorg.conf file the command is:```
cat /etc/X11/**x**org.conf
```Linux names are case sensitive.

---

### Post by JPKowal on 2010-01-17
I'll try that. TYVM!

---

### Post by mountforddrive on 2010-01-31
From what I have read in other posts, there is apparently a problem with bandwidth on the SiS card and you will not be able to fix the flickering properly.

I have found that by **removing** the SiS driver will make it work a whole lot better. Use System-> Administration -> Synaptic Package Manager and search for SiS and remove it completely.

You will get rid of the vertical lines and constant flicker but you will still get some flicker from time to time (like a faulty monitor). This will go a long way to stopping your migraines but the only solution is to install a decent graphics card.

---

### Post by JPKowal on 2010-01-31
OK. I downloaded the package and it said it was already installed. So that didn't help. (Sorry for the long wait but I've been busy with school.)

So you can have a driver package installed, but the device still be unclaimed or not have a driver for it, right? In other words, the package does not work. Or is there something else I am missing? I posted xorg.cnf for you.

I guess I will try mount's advice posted in this thread, but he's saying to remove the driver. What driver. There is no driver for the unclaimed device according to you. Or I guess he means remove the package. I guess I will try that.

I guess I will try

# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by JPKowal on 2010-01-31
Oh...and my graphic card works fine for any other OS. I am not playing games or using AutoCAD on this. Please don't tell me to buy anything when I don't need to. That's not why am I here.

---

### Post by cprivers on 2010-02-14
I have the same problem trying to reconfigure the xserver. The command does nothing. I moved the disk to another computer with an on-board video and I am trying to reconfigure it. I have used the dpkg-reconfigure many times before with versions 7.04 and 8.10, but in 9.10 is doesn't work for me. I also do NOT have a /etc/X11/xorg.conf file. The on-board video is an Intel 82865G. I need to get the resolution to 1024 x 768, but the max allowable right now is 800 x 600.

---

### Post by doswald on 2010-03-11
yeah - I have the same problem as well on an HP Pavilion s7410n ...

stuck in 800x600 - but no flickering

dpkg-reconfigure xserver-xorg does nothing

no xorg.conf file on the machine either (ubuntu 9.10)

~# cat /etc/issue
Ubuntu 9.10 \n \l

# uname -a
Linux machname 2.6.31-20-generic 

# lspci | egrep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

# lshw -C display
  *-display
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:cfe80000-cfefffff ioport:c800(size=8) memory:d0000000-dfffffff(prefetchable) memory:cfe40000-cfe7ffff

# cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory

and no - Im not going to install a new adapter or buy a newer monitor...

---

### Post by doswald on 2010-03-11
I hope im not hijacking this thread - but I just saw something interesting... I wanted to share with everyone...

I just migrated my friends little HP over from XP to ubuntu 9.10 - I also installed the edubuntu stack as well for her kids.

I explained to her, Im working on this crappy 800x600 thing. She said that's fine (for now) I need to get to my email  - ill take it now, but if I learn anything she will do a reverse VNC and send me her remote desktop so I can work the issue remotely.

But before she took it home - I unplugged my 17" LG Flatron LCD screen - and plugged in an old Sony Trinitron 17 200GS CRT Tube to it and rebooted... ( I can provide specific model numbers if needed).

wow ... 
The machine came up in 1024x768 automatically ... hmmmm... Went into the settings and saw many resolutions which were exactly what I expect to see. testing all the way to 1280x1024... looked great...

I then swapped the CRT for the LCD - and everything looked even better'er... Thinking I had solved the problem... I then rebooted the box thie the LG LCD again - and Im back to 800x600 again. (also having 640x480 btw - who cares)

check this out ...

While the machine is running and logged in (in 800x600) - I swap the LCD for the SONY 200GS monitor... and WHAMMO the display settings app identifies the Sony monitor (puts the word SONY in the little pink box for me) - and gives me all the wonderful resolutions again... 

PLEASE NOTE - I did NOT reboot, and I did NOT log out... I simply swapped the monitors.

I then put the LCD back - and all resolutions stay available to me ...

I dont know anything about how these monitors are polled for their capabilities - but obviously the old Sony CRT provides the correct info where as the LG LCD does not (for whatever reason).

I hope this might help someone else down the road.

Dave O.

---

