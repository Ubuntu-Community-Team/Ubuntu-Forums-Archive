---
title: "Alienware M9700"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by Thokar on 2007-07-26
All,

     Need some help with something I can't seem to work through.  I'm normally the type of person who likes to solve things myself but I can't seem to find a "working" answer to this one.  I have an Alienware M9700 with an nvidia 7900 GS SLI setup that I just can't get to boot/install Ubuntu.  I've tried just about everything and am at my wits end with this one.  After booting with the CD in the drive, I get the appropriate screen to come up.  After selecting run/install ubuntu, it starts to load a bunch of files and after a min or so the screen just goes black.  I never hear any audio so I don't think it's loading all the way up.  I'm still thinking it has something to do with my video card/drivers but I've tried everything I can think of to fix it.  I've read a few posts where people with the same or identical setup have had the same or similar issues but what they recommended didn't work for me.  I'm trying to install Feisty Fawn and dual boot it with Vista if that helps any.  Any help is greatly appreciated.  Thanks.

---

### Post by DJMatty on 2007-07-26
Have you tried booting the live cd using the safe graphics mode? That will run it using the vesa driver, which was the only way I could get ubuntu live cd to work on my machine that has an nvidia 8800GTX card in it.

Once you get to the live cd boot, you can install it with the vesa driver, reboot into your installed o/s and then install envy and get that to install the proper nvidia drivers.

Cheers

Matt

---

### Post by TDub on 2007-10-04
The Alienware laptops are a real pain with Ubuntu at the mo (hopefully gutsy will be better). Most problems are fixable.

Have you tried any of the methods on [this thread]("http://ubuntuforums.org/showthread.php?t=233340") to get into the Live CD?

if just want to install and don't care about the live cd, download the [Ubuntu Alternate CD (check box at bottom of form)]("http://www.ubuntu.com/getubuntu/download") with a text based install.

Also [see this thread]("http://ubuntuforums.org/showthread.php?t=555008&highlight=m9700") if you have problems with your WiFi

TDub

---

