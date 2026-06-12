---
title: "Only Safe Graphics Mode Working"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by merlinus on 2007-05-06
Running he Ubuntu CD in normal mode left me with a blank screen, and it would only load in safe graphics mode.  I am therefore quite leery of trying to install it on my hard drive.

Suggestions welcome!

Many thanks....

-merlin

---

### Post by jerrylamos on 2007-05-06
Which level of Ubuntu are you trying - Dapper 6.06, Edgy 6.10, Feisty 7.04?

Anyway what worked for me - start in whatever mode will work

Ctrl-Alt-F1

should get you a command line and otherwise black screen

sudo dpkg-reconfigure -phigh xserver-xorg

This should get you some menus where you can select which graphics driver you want to use, for example for me on an Intel 82845G motherboard graphics chip it was i810, on an ATI Radeon RV100 its ati
You might have to look at your BIOS as you boot up, or do
lspci
which should give you the VGA compatible controller, and you even might have to browse the internet at the graphics controller manufacturer site to figure out what graphics driver to use

Select what screen resolution you want example for me was 1280x1024 on a 17" LCD screen

Assuming this finishes O.K. then stop the current graphics screen

sudo killall gdm

and re-start the X server

sudo startx

Now once installed you only do this once.  On CD Live you'd have to do it every time....

Cheers, Jerry

---

### Post by merlinus on 2007-05-06
Thanks very much for your suggestions.

Interestingly, having gotten the livecd to boot up in safe graphics mode, /etc/X11/xorg.conf shows it has correctly identified the monitor, graphics card and resolution.

So I will go ahead and install feisty, and hope for the best.

-merlin

---

