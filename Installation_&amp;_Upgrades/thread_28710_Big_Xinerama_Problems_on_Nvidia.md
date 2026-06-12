---
title: "Big Xinerama Problems on Nvidia"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by hds on 2005-04-21
Hi, 

okay, i've been looking for quite a while now, trying a lot of stuff but none works.

My system: Ubuntu 5.04, Athlon Xp 2800+,Nvidia Geforce 5200, one LG 1710B 17" LCD  on the DVI-Out (1280x1024) and one Acer FP563 15" LCD on the VGA-Out (1024x768)

Preferred Setup: LG Monitor as primary working monitor, 2nd display as secondary, rarely used information-monitor (and maybe for watching movies while working). 


Now I have the following problems: 

I installed the nvidia-glx - drivers and enabled them with
apt-get install nvidia-glx 
and 
nvidia-glx-config enable

Then I changed my xorg.conf's Device Section to
Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Result: now the VGA is screen one, DVI is dead.

Then I added a second Screen with appropriate values, called it Screen2 and 
set them up in the ServerLayout-Section to the usual

Screen "Default Screen"
Screen "Screen" LeftOf "Default Screen"

Nothing happened.

I also tried almost every combination of

Option Xinerama "on" (and "off"), Option Clone "on" (and "off")
and, because I found it in the Howto: 
         Option      "TwinView"                 "true"
         Option      "RenderAccel"              "true"
         Option      "UseEdidFreqs"             "true"
         Option      "MetaModes"                "1600x1200,1600x1200;1280x1024,1280x1024;1024x768,NULL;800x600,800x600;640x480,640x480"

in the appropriate Device-Section of the Video Card. 

The only thing that happened, while using MetaModes was that the DVI worked again (nothing with the VGA though) and the screen was somehow scrollable vertically and had about double the normal size..

Well, now I have no Idea anymore. Anybody able to help me? Would be really great.

Regards, 

Julian

---

