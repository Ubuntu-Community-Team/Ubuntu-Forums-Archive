---
title: "Radeon 9600 - Configuring X11 - r300g video driver - Ubuntu 10.10 powerpc"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by 1984dc on 2011-04-06
Hello every one here on the forums!

I am trying to set ubuntu up on my powermac g5 and I am having some trouble configuring X. When i boot Yaboot is fine and then i get a bit of splash then black :confused:

I tried just putting the following example of xorg.conf in the /etc/X11 but I still get a blank screen on boot. I think that is because the radeon-kms driver isn´t installed.
[http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx](http://mac.linux.be/content/xorgconf-ppc-machines-radeon-9600-and-kms-kernel-lucid-lynx)

So i did a bit of googling and i found this documentation from Ubuntu.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

It suggested the r300g driver  would work.

So  I tried to purge the old driver by 

```
sudo apt-get remove --purge fglrx
```but i don´t think the fglrx is the right driver on Ubuntu powerpc as it wouldn't purge! How can i find out what driver I am currently using or purge the driver without being specific?



Is it also possible to install the r300g through apt-get? I think that would be better for me as I am in a "bare bones" system. So would the code would be ;

```
sudo apt-get install libgl1- mesa-dri/lucid libgl1-mesa-dri-dbg/lucid libgl1-mesa-glx/lucid libgl1-mesa-glx-dbg/lucid libglu1-mesa/lucid mesa-utils/lucid
```Which was taken from;

[https://launchpad.net/~xorg-edgers/+archive/radeon]("https://launchpad.net/%7Exorg-edgers/+archive/radeon")

Is there any other configuration i need to do after that like  reconfigure the xorg.conf file? What would be my best options for the xorg.conf? Any help on this would be hugely appreciated I've never configured X before, still a bit of a noob two years down the line!

Here´s some details of my set-up;

ATI Radeon 9600:

  Chipset Model:    ATY,RV351
  Type:    Display
  Bus:    AGP
  Slot:    SLOT-1
  VRAM (Total):    128 MB
  Vendor:    ATI (0x1002)
  Device ID:    0x4150
  Revision ID:    0x0000
  ROM Revision:    113-A58504-113
  
Displays: Pennon PVHK-H0781A
1780:
  Resolution:    1024 x 768 @ 60 Hz
  Depth:    32-Bit Color
  Core Image:    Hardware Accelerated
  Main Display:    Yes
  Mirror:    Off
  Online:    Yes
  Quartz Extreme:    Supported
  Rotation:    Supported
Display Connector:
  Status:    No Display Connected

Many, many, many thanks

dc

---

### Post by Iowan on 2011-04-06
Duplicate:
[http://ubuntuforums.org/showthread.php?t=1723067]("http://ubuntuforums.org/showthread.php?t=1723067")

From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

