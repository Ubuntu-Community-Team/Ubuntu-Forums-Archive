---
title: "Gnome / Xorg slow after update to feisty"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by vav on 2007-03-24
I just upgraded to Feisty using gksudo update-manager -c -d... 

Upgrade went through. Initially it told me that nautilus-cd-burner and hence ubuntu-desktop couldnt be installed, but a manual synaptic reinstall worked perfectly.

Currently my problem is that the UI has slowed down. e.g. if I move the firefox window around, it doesnt repaint quickly, and leaves a trail of half broken window frames for a second or so before re-painting. The only other application I'm running concurrently is amarok.

I ran top in a terminal while doing this and noticed that the xorg process starts taking >80% of CPU when I simply move a window around. 
Compiz or Beryl are not enabled.

What could be the issue? Is gnome 2.18/ xorg 7.2 expected to be slow? Or is this just a beta problem?

My laptop's an inspiron 9300 with 768MB RAM, 2GHz Pentium M, ATI Radeon m300.

Thanks

---

### Post by stateq2 on 2007-03-24
I've been having the exact same problems.  At first, I figured it was firefox...but after using other browsers, I found that it wasn't the problem.  Then I thought it was gnome...but that doesn't seem to be the issue either, because I've experienced the same slowness, choppy window repainting, etc when using other window managers such as openbox and fvwm.  Obviously running beryl makes it much worse.  Anyone have any ideas?

My laptop's a compaq evo n800c, 1.7ghz p4, 768mb ram, ati radeon mobility 7500

---

### Post by ubuSenshi on 2007-03-25
Same problem here. When I start Firefox or any other browser (tried some) my Xorg process uses up to 90% of my CPU.
I'm running Beryl with AIGLX, but it also happens if I disable Beryl (in my Session-Settings).
I upgraded from Edgy via the update-manager few weeks ago (to Herd4) and at this time everything worked fine. Must be something in Xorg.

My laptop: Gericom Cinema XXL 05360, 2.53GHz Intel Celeron 325J, 512MB RAM, ATI Mobility Radeon 9550

---

### Post by stateq2 on 2007-03-25
Well, the problem is definitely w/ xorg, but I found a work around.  I commented out all of the lines that I added from the 
[beryl/feisty wiki page]("https://wiki.ubuntu.com/BerylOnFeisty#head-bb7661a4cb9eafe481a1088f578ee3a287f9347d-2")...then xorg, gnome, firefox, etc., worked as usual.  Although, beryl doesn't work properly now...but at least everything else is back to normal.

These are the lines that I commented out in my xorg.conf file:
```

#Option "DRI" "true"
#Option "ColorTiling" "on"
#Option "EnablePageFlip" "true"
#Option "AccelMethod" "EXA"
#Option "EXANoOffscreenPixmaps"
#Option "RenderAccel" "true"
#Option "AGPFastWrite" "on"

```

I hope this works for others...I also noticed that everyone that posted so far about this have laptops w/ ati radeon cards...maybe this problem is limited to us :confused:

---

### Post by brink on 2007-03-29
I had the same problem (with ATI Radeon 9600). Solved it and was able to run beryl with the following

Section "Device"
   Driver          "radeon"
   Option "DRI" "true"
  Option "ColorTiling" "on"
  Option "EnablePageFlip" "true"
  #Option "AccelMethod" "EXA"
  Option "EXANoOffscreenPixmaps"
  #Option "RenderAccel" "true"
  Option "XAANoOffscreenPixmaps" "true"
 ...

 
Section "Extensions"
         Option "Composite" "On"
 EndSection



I never had this option. Not messing with it.
#Option "AGPFastWrite" "on"


No slowdowns. I'm not totally down with xorg setups, but I have the feeling that EXANoOffsScreenPixmaps doesn't actually do anything since EXA isn't enabled.

ps. oh, this is on a desktop system, so it isn't just limited to laptop ati cards.

---

### Post by opossumjack on 2007-04-21
I've done as brink said... 

IT WORKS PERFECTLY!!!

I also have a Radeon on a desktop...

thanks a lot guys...

---

