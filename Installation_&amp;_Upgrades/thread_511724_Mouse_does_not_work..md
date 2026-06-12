---
title: "Mouse does not work."
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by CodyJ on 2007-07-28
I've googled and searched and searched. I have an old CTX pc w/ an AMD that has a varied ram amount value(because I am interchanging ram to get this installed).

Okay I am installing Xubuntu(its installed -- thank god).

I can get to xserver now, finally. I then am like, YES ITS INSTALLED. :lolflag:

Think again, my mouse did not work. I have tried psaux, input/mice... its a PS/2 mouse. I can't get it working. ANY help is appreciated. Thank you.

---

### Post by CodyJ on 2007-07-28
*bump*

---

### Post by rillip on 2007-07-29
not to sound dumb, you're sure the mouse works?  Ps/2 mouse is like... duh.  No way that got overlooked, I don't think.  Might check your bios for legacy support?

---

### Post by CodyJ on 2007-07-29
The pc is older and doesn't even have usb ports... but just to let everyone know. I messed up the pc somehow. I think the motherboard went shot... don't know why.

---

### Post by rillip on 2007-07-29
fragged mobo is the leading cause of ps2 mouse failure I hear. :D  Sorry to hear about your now dead computer though :(

---

### Post by CodyJ on 2007-07-30
No, I think it was one of my stupid mistakes... I was messing with the hdd bay drive (making some leet wires because I make my own rounded IDE cables with a knife and tape. Well, I took the PSU out for maybe switching and that went good, took out the drive bay and I kinda hit the motherboard (near the ram slot... but this motherboard has nothing their its basically the end of it so I thought nothing of it. It could be the switch to the motherboard because I did take it out, but no idea. I will have to test it. I don't care for this pc anymore since it would not run my requested os so the hell with it. If anyone wants an old AMD 6-K let me know, pay 5 bucks and shipping and its yours. Case and motherboard included. Or w/e you want.

---

### Post by CodyJ on 2007-07-31
Correction, it was the power switch !!! 

Believe it or not, I spliced the wires, and hot-wired it, viola powered up. 

It had an option in BIOS for os support or something... I enabled it, options were non-os/2 or os/2 or something like that. Anyhow I haven't mounted the HDD yet but hope when I do and get more ram from a buddy (i have to replace the psu fan and cpu fan, too old and to loud...) that it works.

---

### Post by lisati on 2007-07-31
> **CodyJ said:**
> Correction, it was the power switch !!! 

Believe it or not, I spliced the wires, and hot-wired it, viola powered up. 

It had an option in BIOS for os support or something... I enabled it, options were non-os/2 or os/2 or something like that. Anyhow I haven't mounted the HDD yet but hope when I do and get more ram from a buddy (i have to replace the psu fan and cpu fan, too old and to loud...) that it works.

Did you really mean os/2, it's something different to ps/2......

EDIT: os/2 is an operating system, ps/2 a style of connector. If it's ps/2 mentioned in your BIOS I'd recommend leaving it enabled if that's the kind of mouse you have

---

### Post by CodyJ on 2007-07-31
Some reason... Xubuntu no longer boots up, I tried recover and it went to load and then a kernal panic. I had the IDE cable backwards somehow the first time or something, then i did something and it changed and a buncha messing around... I guess I will re-install Xubuntu. Maybe my mouse will work then!

---

### Post by CodyJ on 2007-07-31
And the problem continues... !

I think the motherboard does not like he fact I am going to make it run, I think the switch went bad again. I don't think its to deal with the PSU(tried others) so it has to be the switch being messed up by the motherboard, time to use a flip switch!

---

### Post by gridsleep on 2007-08-07
7.04 Feisty Fawn has a glitch in the PS/2 drivers.  See elsewhere in the forums (I was reading it a while ago but didn't keep track of the page url).  The problem has been fixed for most real world hard wired PS/2 but not for Virtual PS/2.  It doesn't matter what kind of physical mouse you are using, the Virtual PC 2007 gives Ubuntu a PS/2 mouse to use and Ubuntu does not recognize it.  I have not found any info on a fix yet, probably still in progress (and probably low priority).  Work around for now is to enable Mousekeys via <right alt-F1> (to get menu) "System -> Preferences -> Accessibility -> Keyboard Accessiblity".  Put a check mark in "Enable keyboard accessiblity features" using spacebar.  Tab down to the tabs, right arrow to "Mouse Keys".  Tab down to "Enable Mouse Keys" and spacebar to activate or use "M".  Tab to "Close".  Use <right alt-F1> again and go to the bottom of the System menu to reboot.  After that you can use the numeric keypad to move the mouse around.  Then, wait for a fix.

I had the 6.16 installed previously and it worked perfectly.  After upgrading to 7.04 (and finding out I need to turn off Hardware Virtualization on my particular computer to allow Ubuntu to boot up), there is no mouse.  There will be no mouse until a patch is released.  C'est la vie.

---

