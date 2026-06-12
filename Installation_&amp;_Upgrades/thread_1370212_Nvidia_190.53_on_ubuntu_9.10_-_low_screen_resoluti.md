---
title: "Nvidia 190.53 on ubuntu 9.10 - low screen resolution"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by c800957276 on 2010-01-02
Hello,
I am an absolute newbie here.  I installed Ubuntu 9.10 on my laptop and worked wonderfully, basically plug and play, so I decided to install 9.10 on a PC that I have connected to a 32 inch 16:9 LCD TV that I use for movies.
This PC is an IBM Netvista 8303 KKU with a 512 MB NVIDIA GeForce 8400.
The TV is a no-name brand (Astar) that I've had for 3 years so far.
Anyway, after I installed Ubuntu I downloaded the latest NVIDIA Linux Driver from nvidia.com and installed it.  The screen resolution after the install is so low that I can't get it to work properly on my tv.  When I plug a BenQ LCD monitor the NVIDIA X Server Settings utility recognizes that brand and model and I get a bunch of available resolutions.  When I connect my TV, the utility detects a CRT monitor and I can't get more than 640x480 on a 4:3 format instead of the 16:9.  How do I enable higher resolutions on a 16:9 format for my TV?
Please help!

---

### Post by owenisred on 2010-01-03
i dont know if this will help you but try 

[http://ubuntuforums.org/showthread.php?t=1371715&highlight=resolution](http://ubuntuforums.org/showthread.php?t=1371715&highlight=resolution)

---

### Post by c800957276 on 2010-01-04
> **owenisred said:**
> i dont know if this will help you but try 

[http://ubuntuforums.org/showthread.php?t=1371715&highlight=resolution](http://ubuntuforums.org/showthread.php?t=1371715&highlight=resolution)

Thanks,
I don't know if this will work, as my problem is resolution with a third party video card, not one that is integrated as you seem to have, but thanks anyway.

---

### Post by c800957276 on 2010-01-04
OK,
Although I'm a newbie at this, I played with the xorg.conf file and did some changes, after which I got a warning saying that ubuntu was running in low resolution mode.  I was given the option to use the backed up xorg file, but that did nothing, so I reinstalled the nvidia driver in verbose without X running (God, it sounds like I know what I'm doing).

If anyone has any idea about how to manipulate xorg.conf, please take a look at what I did here, and please suggest changes.  I hope to get it working.
If this helps anyone trying to help me, this is what my original xorg.conf looked like, followed by the one i tried to modify:

<code>Section "Monitor" 
Identifier "Monitor0" 
VendorName "Unknown" 
ModelName "Unknown" 
HorizSync 28.0 - 33.0 
VertRefresh 43.0 - 72.0 
Option "DPMS" 
EndSection 

Section "Device" 
Identifier "Device0" 
Driver "nvidia" 
VendorName "NVIDIA Corporation" 
EndSection 

Section "Screen" 
Identifier "Screen0" 
Device "Device0" 
Monitor "Monitor0" 
DefaultDepth 24 
SubSection "Display" 
Depth 24 
EndSubSection 
EndSection 

THE XORG.CONF I MODIFIED:
Section "Monitor" 
Identifier "LVT-32ASB" 
VendorName "ASTAR" 
ModelName "LVT-32ASB" 
HorizSync 28 - 101 
VertRefresh 60 - 160 
Modeline "1360x768@60" 84.5 1360 1392 1712 1744 768 783 791 807 
Option "DPMS" 
EndSection 

Section "Device" 
Identifier "Device0" 
Driver "nvidia" 
VendorName "NVIDIA Corporation" 
EndSection 

Section "Screen" 
Identifier "Default Screen" 
Device "Device0" 
Monitor "LVT-32ASB" 
DefaultDepth 24 
SubSection "Display" 
Depth 24 
Modes "1360x768@60" 84.50 1360 1392 1712 1744 768 783 791 807 
EndSubSection 
EndSection<code>

Thanks!

---

### Post by c800957276 on 2010-01-05
Really, nobody?

---

### Post by ElSlunko on 2010-01-06
If you don't need the latest drivers, try uninstalling the current one and installing the one Ubuntu suggests in System > Administration > Hardware Drivers. I personally need the latest because for some reason the default ubuntu ones would freeze randomly.

If you indeed need the latest make sure you uninstall all versions of the driver via synaptic (just do a search for nvidia) and then try the driver from nvidia.com.

---

### Post by c800957276 on 2010-01-06
I'm trying a fresh installation tonight.

---

### Post by c800957276 on 2010-01-07
fresh intallation did not work at all.  I'm out.

---

### Post by ratcheer on 2010-01-07
I always install my nVidia drivers, manually, and it always works. Do you have a .run file of your driver? If yes, then:

Ctrl-Alt-F1 (to go to a system console terminal)
cd (to the location of the .run file)
sudo service gdm stop
sudo sh ./xxxxxxx.run (to install the driver)
When the installation script asks if you want to autoconfigure xorg, select Yes
sudo init 6 (to reboot)

You should come up in hi-res graphics mode.

Tim

---

### Post by c800957276 on 2010-01-08
Did all that.  It works if I do it when I have a 17 inch 4:3 BenQ monitor plugged during install.
Since I plug this PC to a TV permanently, I did the whole install with the TV plugged to the PC.  For some reason, it does not recognize the TV as an LCD but as a CRT and that's where the problems start.
I agree, Ubuntu works with NVIDIA if the monitor is properly autodetected.  Since my TV is a no-name one, I guess that's the problem and autodetection does not work.
Any ideas?

---

### Post by ratcheer on 2010-01-08
Yes, if you know the correct resolution and refresh rate for the TV as a PC monitor, you can start "gksudo nvidia-settings" and select the proper settings, then save them to your X configuration file.

Be careful, because if you don't know the correct refresh rate and guess at one that is too fast, you can damage the TV.

Tim

---

### Post by hantechbl on 2010-01-08
There is a awesome tool for changing resolutions.  It is called xrandr so if you run xrandr it will say what resolutions you can have.  Then type xrandr -s 1111x1111 and replace the 1s with your resolution.  I hope that this helps you.

---

### Post by spotspot on 2010-01-17
Thanks for those instructions Tim, i was able to install 190.53 smoothly.

However I didn't solve my real problem:  I am trying to play videos with mplayer and vdpau.  I was getting some crashes with the default server, and the latest is even worse, especially with videos from x264.

I have a Revo with the ION chipset.

---

### Post by ratcheer on 2010-01-18
You are welcome.

Tim

---

