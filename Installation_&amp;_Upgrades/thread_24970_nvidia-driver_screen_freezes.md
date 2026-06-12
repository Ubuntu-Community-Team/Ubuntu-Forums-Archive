---
title: "nvidia-driver: screen freezes"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by claudius on 2005-04-08
Hello Forum, 
I installed the nvidia drivers with apt-get. When x is starting the screen turns white and the system freezes. 
... to install the nvidia drivers I did:
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable

I've got a geforce 4 ti 4200. I had the same problems with the release candidate of Hoary and wasn't able to solve the problem ([here](http://ubuntuforums.org/showthread.php?t=24480) 's the link to the post). 

It would be really, really nice if you could help me - I've been trying around with those nvidia-drivers for much too long now!
thanx a lot! :-)

---

### Post by claudius on 2005-04-08
... what might help you from my /var/log/Xorg.0.log :

...
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(WW) NVIDIA(0): config file hsync range 30-86kHz not within DDC hsync ranges.
(WW) NVIDIA(0): config file vrefresh range 50-180Hz not within DDC vrefresh ranges.
(II) NVIDIA(0): Standardbildschirm: Using hsync range of 30.00-86.00 kHz
(II) NVIDIA(0): Standardbildschirm: Using vrefresh range of 50.00-180.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 350.00 MHz
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "928x696" (height 1392 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "896x672" (height 1344 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1200)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
...
and:
...
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
...

I'd be thankful about any help!!! Thanx in advance! 
ps: I added my xorg.conf - maybe it helps!

---

### Post by claudius on 2005-04-09
I just wanted to check glxgears. ... I got quite an interesting error-output. It doesn't tell me a lot, but maybe it says something to you: 

cl@clc:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
glxgears: Error: couldn't get an RGB, Double-buffered visual.


glxinfo told me:

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Speicherzugriffsfehler

... you know what is the problem and how I could fix it?
thx a lot!

---

### Post by c_dog on 2005-04-09
Looks like we'll have to see your /etc/X11/xorg.conf file in order to help you with this one. Form the Xorg.0.log there's some problems there.

---

### Post by claudius on 2005-04-09
here is the xorg.conf. Thanx a lot!

---

### Post by claudius on 2005-04-09
problem solved: 
I simply added 
Option "nvagp" "0" 
to the nvidia-driver-part in the xorg.conf

---

