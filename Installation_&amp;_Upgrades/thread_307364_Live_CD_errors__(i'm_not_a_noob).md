---
title: "Live CD errors  (i'm not a noob)"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by CyberCod on 2006-11-26
I've successfully installed ubuntu on my machine, edubuntu on my 4-year-old son's machine, and now i'm tying to install ubuntu on my Mother-in-law's machine.

In booting from the live disk, i get the normal option screen,
and it starts to load, then after a moment it starts filling up the screen at very high speed, and i can't make out much of what it is there but i've squinted out a few lines of the message (its repeating over and over:

IRQ LOCKUP,cleared.. (a bunch more stuff, then) VSYNC, FBUS, RISC  (and more)


its two lines superimposed by the fast scrolling and pause/break doesn't work.



This is on a modified Compaq (cringe) Presario with a 700mhz Pentium 3.  Plenty of drive space.

The diskchecking utility runs fine and finds no errors, I've tried 7 different disks. (i had 10 shipped to me) and last night i downloaded a new ISO and have tried that with the same result.

If you guys need more hardware info, just ask  i can get specifics for you.

If you DON'T know how to help me, please bump me up so someone else may see it and be able to...  often hard problems get buried here with no responses because initial viewers are stumped.

Thanx for your time, i am hoping this works out... she's been waiting 3 weeks for her computer back.](*,)

---

### Post by meng on 2006-11-26
How much RAM does this puppy have? One option is to try the Alternate CD instead of the LiveCD. The installer is practically identical.

---

### Post by CyberCod on 2006-11-26
Its got 384MB... and i thought of the alternate CD, but if i get it installed that way, then the same conflict would feasibly keep me from getting it booted up.  so i've been leary of trying that route because then i have to remove and re-install everything just to get back to Win-only system if it didn't work.

I've used the Alt CD for edubuntu on my son's PC as that system was too old to run live CD and installer with any stability.

I'm not ruling the Alt CD out, but i wanna talk to someone who's seen this before if possible before i go that route.

Thanx for the quick reply btw.


 some more hardware info below.
please excuse poor typing.

Motherboard:   Compaq 0588h
Bios:  Compaq 686C3
Onboard Graffix:  Intel(r) 82810E Graphics Controller
Graphics card:  Ati Radeon 7000VE

---

### Post by louieb on 2006-11-26
That's not bad 2 PCs out of three installed with little problem. 
A P3 700 MHz 384 MB ram should run the Live CD OK. 
Check out this [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and see if you can find a work around here. 
This page lists the most common options needed to boot machines with weird hardware or a flaky BIOS.

---

### Post by CyberCod on 2006-11-26
tried a few of the boot options, namely 

noapic nolapic noapci

which sounds like something from Harry Potter.

I seemed to get past where i was, but only end up with a blank-screened system lock.

I've got some ideas to try, like removing all non-essential cards and adjusting IRQs in the extremely stripped-down BIOS.  But thats going to have to wait temporarily.  I'm also going to look for an updated BIOS.  If anyone has any more suggestions, i'm all ears.

---

### Post by CyberCod on 2006-12-04
*UPDATE*

After removing all pci cards and defaulting the bios to onboard video and sound, Ubuntu installed like a dream.  After it was up and running, i changed the settings in /etc/X11/xorg.conf to reflect the PCI video card and its slot number (the slot was hard to figure out) and then rebooted, installed all the appropriate cards and all is running fine.

I have since had trouble trying to install splashy, as it says it conflicts with itself (weird? it thought so too).  But i abandoned splashy and went back to usplash for simplicity's sake, and because splashy seems to be a little volatile right now as far as development goes.

Otherwise everything seems to be A-OK.

Thanx for your attentiveness, and attempted help.

If someone else is trying to install on this particular model of system, just remove all cards and change bios back to default settings, things should go fine from there.

Thanx again. 

Jeff

---

