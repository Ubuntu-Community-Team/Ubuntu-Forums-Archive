---
title: "Black screen when X starts (but mouse is working)"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by V-Turn on 2005-08-28
Hi,

I have installed Ubuntu this week-end, but was unfortunately unable to start the system, here is what happens :
 - the system boots, everything seems to work fine
 - then X starts, which also seems to work fine
 - I see my mouse cursor on the screen, it is fully functional
 - but then... nothing more there is no background, window, anything on the "desktop". I can drag the mouse around, but it does not respond to clicks. And ever more strange : the CTRL+ALT+BKSP does not seem to do anything either (so I can't exit X and look for the log file).
I am basically stuck with a black screen and a fully functional mouse cursor. Fun, but well...

It is the exact same thing with the Live CD. I even tried the latest breezie install CD from today (08/28), but again, black screen with mouse working.

It is not my machine, since I was able to fully use [flash linux](http://flashlinux.org.uk/), so maybe somebody is able to guide me further (should I try an expert install, and what options should I change)?

Hardware details :
CPU : Athlon 2000+
MB : ASUSTeK A7V880 (VIA KT880)
Video : HIS Excalibur 9250 - 128 Mo TV-Out/DVI (ATI Radeon 9250)

Thank you for your help.

V.

---

### Post by V-Turn on 2005-08-29
I tried the Gnome live CD also (based on Ubuntu), still no luck. Same thing, despite using the live-expert mode, and conservative settings for the X configuration.
Note that X does seem to start fine, and the mouse is working it is just that "what's next" (Windows manager?) is not starting. And the system still does not respond to CTRL+ALT+DEL/BKSP, which is strange and annoying...
I used this opportunity to take a screenshot
[IMG]http://v.turn.free.fr/DSC00990.jpg[/IMG]

Any idea, anyone?...

---

### Post by Thulemanden on 2005-09-12
Try different video drivers, either select ati or radion or vesa.

---

### Post by yrjo on 2005-09-12
When your computer starts press ESC. Take failsafe mode. You will be in
textmode. sudo dpkg-reconfigure xserver-xorg
Then you can configure your x right, take radeon module it should work fine.

---

