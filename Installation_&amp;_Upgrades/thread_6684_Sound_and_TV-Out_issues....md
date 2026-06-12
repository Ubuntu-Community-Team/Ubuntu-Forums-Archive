---
title: "Sound and TV-Out issues..."
date: 2004-11-30
forum: Installation &amp; Upgrades
---

### Post by WiLLiE on 2004-11-30
How do I get this to work?:

1. 

Edit:
All solved, but 2 things..
1. How do I enable nForce2 hardware AC3 encoding on-the-fly (if possible)
2. How do I set Gnome to use Alsa instead of ESD

---------------------------------------------------------------------------
2. I want to use the TV-Out of my card (nVidia GF4).

I've gotten it to work somewhat, altough it stretches the desktop between my monitor and my TV.

In windows I have to 2 seperate desktops with seperate resolutions, eg. 1280x1024 on my CRT and 1024x768 on my TV.
Can I have that in Ubuntu? I don't want the desktop streched for obvious reasons. (I only watch movies on my TV)

I followed the Guide in the FAQ (forum) when I installed the nVidia driver:

1. sudo apt-get install nvidia-glx
2. sudo nvidia-glx-config enable
3. sudo reboot

Is that enough? or is it better to install them from nVidias site?
---------------------------------------------------------------------------

If you've read all this I'm very greatful.
I can do alot of things on Linux, but I need to know these naggin' questions  :D

---

### Post by Nano on 2004-12-09
[QUOTE=WiLLiE]How do I get this to work?:

1. 

Edit:
All solved, but 2 things..
1. How do I enable nForce2 hardware AC3 encoding on-the-fly (if possible)
2. How do I set Gnome to use Alsa instead of ESD

---------------------------------------------------------------------------
2. I want to use the TV-Out of my card (nVidia GF4).

I've gotten it to work somewhat, altough it stretches the desktop between my monitor and my TV.

In windows I have to 2 seperate desktops with seperate resolutions, eg. 1280x1024 on my CRT and 1024x768 on my TV.
Can I have that in Ubuntu? I don't want the desktop streched for obvious reasons. (I only watch movies on my TV)

I followed the Guide in the FAQ (forum) when I installed the nVidia driver:

1. sudo apt-get install nvidia-glx
2. sudo nvidia-glx-config enable
3. sudo reboot

Is that enough? or is it better to install them from nVidias site?
---------------------------------------------------------------------------

If you've read all this I'm very greatful.
I can do alot of things on Linux, but I need to know these naggin' questions  :D[/QUOTE]
 I found this somewhere:
Section "Device"
  Identifier "nv-go"
  Driver "nvidia"
  VideoRam 65536
  Option "DPMS"
#  Option "NoBandWidthTest" "true"
  Option "CursorShadow" "true"
  Option "RenderAccel" "true"
  Option "NoLogo" "true"
# The following enables TV-out
  Option "TwinView" "true"
  Option "TwinViewOrientation" "Clone"
  Option "TVStandard" "PAL-B"
  Option "SecondMonitorHorizSync" "30-50"
  Option "SecondMonitorVertRefresh" "60"
  Option "MetaModes" "1024x768,1024x768"
EndSection

---

