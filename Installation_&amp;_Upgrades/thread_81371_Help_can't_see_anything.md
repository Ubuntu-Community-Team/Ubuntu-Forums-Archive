---
title: "Help can't see anything"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by ExploringLinxu on 2005-10-24
Hello,

I successfully installed Ubuntu 5.10 on my computer. I have a tft screen that only seems to run in text mode or on 1280 x 1024 resolution. This means I can start Ubuntu in the safe mode, as soon as I start it normally on starting up GNome my screen will display input not supported, I thus assume it is sending a resolution or refresh rate or both that are not supported by the screen. I found several threads on this subject but I don't understand. Some seem to solve resolution problems from within Gnome, which is great but I cannot see anything there. So how to do it while started up in the safe mode. I'm not an experienced linux user.

Thanx!

---

### Post by lisje on 2005-10-24
you might want to try editing your xorg.conf

---

### Post by taurus on 2005-10-24
Look in /etc/X11/xorg.conf especially section about horizontal and vertical refreshing rates!!!
Make sure those numbers are right for your monitor...

---

### Post by ExploringLinxu on 2005-10-24
Thanx a lot! I already figured that one out myself, the question is how. I tried using vi as this I suppose is a editor to use in the text screen environment but guess what it seems to create a new xorg.conf or something because there isn't really much to edit. (lots of black screen).. 
But maybe I'm doing something wrong I'm not so well known to linux

---

### Post by taurus on 2005-10-24
Yes, vi (or vim to be correct) is one of many text editors.  However, if you don't know what you are doing with it, it will beep the heck out of you when you press a wrong key...  Therefore, you may want to try pico instead.  Most of the basic commands are at the bottom of the screen,

sudo pico /etc/X11/xorg.conf

---

### Post by ExploringLinxu on 2005-10-25
Thanx again Taurus, I figured out reading some other forums I could use Nano which was a lot more user friendly as vi. But with the same result. There seems to be no xorg.conf there are no lines when I open it. Probably in my enthousiams I did something wrong although gnome still seems to work hearing from the enthousiastic music it is producing when it starts up. Of course I cannot see anything. 
Question is now how do I get xorg.conf back?

---

### Post by rama on 2005-10-26
Try sudo dpkg-reconfigure xserver-xorg from "safe mode". It did the trick for me. Make sure to input the refresh rates that your tft supports (check your manual). 
In my case though this solution seemed to have a side effect as I get errors when running glxinfo and glxgears. I tried repeating the process of installing NVidia drivers from the step "sudo nvidia-glx-config enable" and I got a black screen once again... any ideas?

---

### Post by Perfect Storm on 2005-10-26
[QUOTE=ExploringLinxu]Thanx again Taurus, I figured out reading some other forums I could use Nano which was a lot more user friendly as vi. But with the same result. There seems to be no xorg.conf there are no lines when I open it. Probably in my enthousiams I did something wrong although gnome still seems to work hearing from the enthousiastic music it is producing when it starts up. Of course I cannot see anything. 
Question is now how do I get xorg.conf back?[/QUOTE]

You properly didn't write it correct. Linux is case sensitive

sudo nano /etc/X11/xorg.conf

---

### Post by ExploringLinxu on 2005-10-27
Thanx again, I indeed missed the case sensitivity.. Thing is I worked through my xorg.conf again, I actually manually fed in the refresh rates and resolution windows is running but the result is the same. I read a post somewhere that the problem might be caused by the DVI cable but this suprises me as it seems to work in text mode.
I really don't know how to solve this one..

---

### Post by ExploringLinxu on 2005-10-28
Despite several attempts still an error starting up my x-windows. Monitor keeps displaying that the input is not supported. In xorg.conf as far as I can judge refreshrate and resolution are set properly. Any suggestions?

---

### Post by rama on 2005-11-02
In my case if I change "nv" to "nvidia" I get a blank screen.

---

### Post by rama on 2005-11-07
I realized that the problem has something to do with the dvi and the analog output of my graphics card. I changed nv to nvidia in xorg.conf and then I changed the cable so that my tft was connected using the analog cable. Is there a way to use the dvi cable?

EDIT: 
RTFM!

The solution is to add : 	Option          "ConnectedMonitor"	"DFP"
```
Section "Device"
	Identifier	"NVIDIA Corporation NV30 [GeForce FX 5800]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
**	Option          "ConnectedMonitor"	"DFP"**
EndSection
```

---

### Post by basse1989 on 2005-11-11
Option          "ConnectedMonitor"	"DFP"
ftw! :D

---

