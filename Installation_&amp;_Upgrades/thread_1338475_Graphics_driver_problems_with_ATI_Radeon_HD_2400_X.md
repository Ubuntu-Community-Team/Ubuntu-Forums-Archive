---
title: "Graphics driver problems with ATI Radeon HD 2400 XT"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by palm_ on 2009-11-26
Hey, I'm trying to get the graphics driver to work. At first, the proprietary drivers for my card worked  fine, but then one day my CPU was at 100% all the time. I managed to fix this by editing  in xorg.conf. As of now it looks like this:

Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    2640 800
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver "ati"
    Option "Accel"
    Option "AccelMethod" "XAA"
    Option        "DRI"            "true"

EndSection

I have tried installing the drivers from ATI's homepage for my card, and i have POSIX enabled. 
I would like to able to use the FGLRX driver, to be able to better run wine and use some desktop effects. 
Does anyone have any ideas as of how this can be done?

---

### Post by darkod on 2009-11-26
Install EnvyNG package with
sudo apt-get install envyng-core envyng-qt

It should appear in Applications -> System Tools

You can also use text mode in terminal with
envyng -t

I had a problem with my integrated HD3200 and I just used it in text mode to download ATI driver, without removing current one. Worked straight away. See if it can help you.

---

### Post by palm_ on 2009-11-26
Running this in text mode worked awesome for me!
Thank you so much!
Desktop effects works, videos run smoother and mu cpu is running at a lower percentage than before.

As for now, I will mark this as solved!

Edit: 
william@william-desktop:~$ glxinfo | grep rendering
direct rendering: Yes

everything looks good to me!

---

### Post by darkod on 2009-11-26
Excellent, glad it could help.

---

### Post by ridgeBoy on 2009-12-11
Hi all!

I was looking for an apropiate grahics driver for my ATI (I own an Acer TravelMate 5720 with an integrated ATI HD 2400 XT ) 

I was so frustrated because I was using Mandriva from 2009.0 and there my X.Org drivers were right. But with 2009.1 3D effects dissapeared, up to the new release (2010.0).

I have had to move to Ubuntu, because I had some home to find a solution and... HERE IT IS!!!!

Lots of thanx for the EnvyNG driver!!! It's awesome. I'm feeling very proud again of my grahics environment.

Really this works :) (At least in Ubuntu 9.10)

:)

---

