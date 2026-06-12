---
title: "Hangs during startup"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by Nahash on 2005-11-19
Hey everyone, 

I just installed Ubuntu on a second hard drive on my PC and dual OSed it with Windows XP. The install and partioning went perfect. It asked to boot without cd so I took it out and it went to the GRUB version 0.95 loader. It chose the normal Ubuntu kernel after 10 seconds, then went though and checked ok for almost everything. The one thing it left completely BLANK was Starting Hotplug subsystem. I went and searched all over the forums, tried about 50 different things, including unplugging everything but the mouse and keyboard (all periphrials other than that unplugged) and it still goes through, leaves "Starting hotplug subsystem..." blank, goes on.....seems to finish, then brings up a black screen with a small white cursor that looks like you can type something in....but about 2 seconds later, it freezes....

I tried going into BIOS and disabling USB and all of that, still got that problem. Can somebody please help me out? I really want to try Ubuntu out....but it doesn't seem to want to work on my machine....

The only problem that I have encountered so far is I have an extra video card (NVIDIA GeForce FX 5200 plugged into PCI slot, Intel(R) 82810E Graphics Controller for onboard video card- disabled through Windows because I couldn't find an option to disable it in BIOS) that is the only possible confliction between hardware I can find. I've unplugged everything and it still doesn't work....(still boots to "Starting hotplug subsystem..." leaves it blank, goes on, gets to the black screen with small white cursor (which apparently you can type things into before it freezes but it clears it when it freezes) and then freezes!) I'm getting desperate to find some kind of answer to this problem. Any help would be greatly appreciated!

~Nahash~

---

### Post by jasper cat on 2005-11-19
Sorry I can't offer a quick fix, but having installed 5.10 on 6 machines I have one which defeats me in this exact same way - looking at others on the forum a common thread seems to be on-board video disabled and a second video card - I too have Nvidia FX5200. Nothing I have tried fixes it.

---

### Post by twbutler on 2005-11-28
I am also having the exact same issue with my system - I am using the live CD of kubuntu 5.10, and when the system is getting ready to start X windows, I get a black screen with the white "cursor" underbar in the top left and then the system hangs!   :confused: 

Here are my specs:
MSI K8N Neo4 Platinum
AMD64 3200+
MSI NX6600LE TD256E Pci-e video card

Any one find a solution? 

Thanks...
T

---

### Post by softgun on 2005-11-29
This seems a common prob with Ubuntu, when looking at forums. I am having a problem booting ubuntu CD, with a warped hourglass like screen. The trouble is, it could be a video card issue or monitor issue. Perhaps the default refresh rates incompatible or certain graphics chips are not recognised.

Any way to figure this out?

---

### Post by root@localhost on 2005-11-29
I'm having the exact same problem as well, and, as of now, have been unable to do anything about. I have two video cards in the computer, one in the motherboard and one in a PCI slot, and would like to use the non-integrated card, which is made by ATI. The computer in question is a 1.7GHz Celeron with 768MB of RAM on a 15" flat panel monitor. If I find anything that works, I'll post back, but so far my PC has been pretty useless for the past few days. No one's replied yet to the other topic where I had this problem a few days ago.

---

### Post by bwog on 2005-11-29
Perhaps this helps when you have two video devices (I didnt try it myself):

 by arkhan_jg (618674) on [http://hardware.slashdot.org/hardware/05/11/13/1635229.shtml?tid=90&tid=137](http://hardware.slashdot.org/hardware/05/11/13/1635229.shtml?tid=90&tid=137)

 If you only want the PCI geforce working, your best bet is simply to disable the onboard graphics in the BIOS.

If you wanted both onboard and PCI graphics card to work (in some form of xinerama setup), set the PCI card to be the default display device in the BIOS, as opposed to AGP (most onboard video chips are classed as AGP devices in the BIOS). A number of PCI graphics cards aren't happy unless they're the first video device to be initialised.

[http://www.techimo.com/forum/t155963.html](http://www.techimo.com/forum/t155963.html)

You can't disable it, and you don't. Point being that you can very well use a PCI card in parallel with the integrated VGA. (And if you plugged an AGP card, the integrated pseudo-AGP unit disappears automatically.)
All you need to do is set the BIOS VGA preference to "PCI" rather than "AGP" so that your PCI card becomes the primary VGA.

Be carefull with BIOS settings.

(I googled for 'disable onboard video pci card ubuntu')

---

