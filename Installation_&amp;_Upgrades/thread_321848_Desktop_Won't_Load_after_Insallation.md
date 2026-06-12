---
title: "Desktop Won't Load after Insallation"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by gr33ny on 2006-12-19
Hi

I downloaded 6.10 and attempted to install Ubunutu using the GUI - however this repeatedly failed after just getting a pink screen after selecting the "Install" option. 

I have now tried text based install which worked perfectly, however I cannot log on.  I enter user/password and the desktop begins to load, but after a few seconds all I get is a pink screen (curser works okay) and nothing else.

I have tried re-installing and also tried logging in using a safe session - this still will not let me log in.

I have an Advent 7066M (laptop) using a SIS 661FX Chipset with integrated graphics, 1.5Ghz Celeron M and 512Mb RAM (32Mb going on video memory).

Any one got any suggestions?

Many thanks

---

### Post by wpshooter on 2006-12-19
Is the computer running any other O/S or are you going to be running only Ubuntu ?

---

### Post by gr33ny on 2006-12-19
Many thanks for your reply

The laptop currently only has Ubuntu running and I will be running no other OS on it

Paul

---

### Post by wpshooter on 2006-12-19
First I assume you are burning your CDs at 4X or less.

Second, that you are checking the integrity of your CDs by running the verification function found on the initial Ubunut boot screen menu.

If all of that is true then try getting the **KILLDISK** program and **WIPE** your hard drive completely clean and then retry the installation from the ALTERNATE (text based) CD.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

Let us know if you get it installed.

---

### Post by gr33ny on 2006-12-20
Many thanks for your reply

I have tried as you suggested but still have exactly the same problem after reinstalling.

I burned the ISO at the slowest possible speed (4X) and checked the disc from the installer screen and it was okay.

Any other ideas?
Paul

---

### Post by MikeDK on 2006-12-20
Hi there have you tried setting the burn-speed at -Auto- I usually do this to make it work so the machine dont burn in a speed the cd-rom cant follow.

U follow??

Best Regards MikeDK

---

### Post by gr33ny on 2006-12-20
Many thanks for your reply, unforutnately I do not have an "Auto" setting on my burner program to try this out with.

Does anyone have any further suggestions?

---

### Post by synogenes on 2007-04-28
> **gr33ny said:**
> Hi

I downloaded 6.10 and attempted to install Ubunutu using the GUI - however this repeatedly failed after just getting a pink screen after selecting the "Install" option. 

I have now tried text based install which worked perfectly, however I cannot log on.  I enter user/password and the desktop begins to load, but after a few seconds all I get is a pink screen (curser works okay) and nothing else.

I have tried re-installing and also tried logging in using a safe session - this still will not let me log in.

I have an Advent 7066M (laptop) using a SIS 661FX Chipset with integrated graphics, 1.5Ghz Celeron M and 512Mb RAM (32Mb going on video memory).

Any one got any suggestions?

Many thanks

It sounds like I have exactly the same laptop with identical problems.  I've tried reinstalling various versions including the version on the DVD from the book Ubuntu Unleashed (yup - I was optimistic and bought a book...) but also downloaded the iso.  I've tried 6.06LTS, 7.0.4, I've tried the SiS driver replacement from Winischhofer.net, been through the logs, tried replacing the "vesa" in the xorg.conf file with "sis" as suggested on various sites, and also with "vga" which supposedly always works.  Nope, nada.

I can get a text-based install but if I run starx it will freeze at a brown screen with a pointer on it.  Ctl-Alt-Backspace will close X but that returns to the graphical logon (which seems to have no problem appearing).

I've also tried updating the xorg.conf file after shutting down X using /etc/init.d/gdm stop, and then restarting it after the xorg.conf file was changed with /etc/init.d/gdm start.

The resolution of the screen on the Advent 7066 is 1280x800 so I've used the command line:
dpkg-reconfigure xserver-xorg
to run the configuration tool and entered the details.  There are three options (simple, medium and advanced) and I've tried the first two.  The third one needs info about the vertical and horizontal refresh rates for the monitor which I can't obtain.  Although the config tool completes, restarting X still locks up.

I've reformatted the partitions and done fresh installs, repeating all the above steps.  I've also tried setting the colour depth to 16 rather than 24 (as someone suggested that might be a problem - no difference) and I even tried removing the sections for depths lower than 8.  No difference.

I tried the variants of the driver compiled for gcc3 and gcc4 on the Winschhofer site - no difference.

I know that SiS don't support Linux but as everyone else seems delighted with Ubuntu and I want some (:( ), I'm on the verge of giving up on the laptop. It runs XP Home on another partition but even though I work with the stuff, I'd dearly like to be free of the MS gunk.

If anyone get's any great ideas about getting Ubuntu up on an Advent 7066, I'm listening too.  Maybe the above will give others a chance to try again what I tried (perhaps successfully) or might stimulate some new ideas.

---

### Post by synogenes on 2007-05-02
I've just tried the noacpi flag on the command line again and this time everything seemed to go through.

The graphics are not the full 1280 x 800 but hey, it's installing.  Looks like everything's fine.  The installer detected my XP partition, guided me in setting up the / and /swap.  All very helpful.  Looks like I'm about to get going.

I've just ordered an Inspiron which I'll be converting to all Ubuntu so I'll be completely free of MS on a machine - that'll be an interesting experience.  No long delays at bootup, continuously waiting for updates and patches to load, all those hogging services running, and wheeee no more licence fees.

The new machine will have Vista on it, but as soon as I have all the graphics and Beryl working, I'll be wondering what it's for and will probably just free up the space.  It feels like the sun has just come out :guitar:

---

