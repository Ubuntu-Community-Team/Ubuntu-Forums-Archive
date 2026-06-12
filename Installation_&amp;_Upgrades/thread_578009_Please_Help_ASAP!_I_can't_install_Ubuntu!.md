---
title: "Please Help ASAP! I can't install Ubuntu!"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by Timothy Benton on 2007-10-16
I'm trying to install the new Ubuntu 7.10 Beta. I had 7.07 running fine but I no longer have the CD, and just formatted the hard drive to freshly install 7.10. I have copies of both the normal and alternate install CDs. When I try to use the Alternate disc everything runs smooth until it comes time to start the OS for the first time. When I use the normal disc it reboots after I click "Start/Install Ubuntu" (or whatever) and the Linux kernel loads. With both discs I get about four lines of "Cannot allocate resource PCI 05894" or something, pretty early in the install process. I don't know what that means but Fiesty Fawn didn't say that.

By the way, I typed this all up on my Wii. I have no computer access right now, so please help!

---

### Post by travm on 2007-10-16
I suggest you boot the live cd in your computer, get your internet back with a keyboard in front of you, and then start asking questions from a working linux environment.  Good luck

---

### Post by Timothy Benton on 2007-10-16
I can't get the LiveCD to start. It just reboots to the Install Menu as soon as it loads the kernel.

---

### Post by travm on 2007-10-16
can you use the alternative cd or the live cd to get you to a command prompt?

also can you be specific about where it goes bad when you install with teh alternative disk?
it may just be a video driver issue. 
Please help us out by listing your hardware, and what the computer told you, or did at the moment it "went wrong"

---

### Post by Timothy Benton on 2007-10-16
i think i can in the alt. cd... why?

---

### Post by travm on 2007-10-16
dude, because that is your "safe mode".  
the command line is how you rescue your system.
you install is probably fine.  you will just need to find the affected driver/module and remove/replace/update depends on what is wrong.  you will be supprised, the command line in linux is far more evolved than dos ever got.  you've got it made as you have the wii to help you along.  I'll explain this to you, this is what I think is going on.  but im not sure since you have given next to no information.
 - ok, you have a video driver problem, which has broken your xorg installation.  but dont fret, it can be fixed, (this is also why you dont install testing versions of software on your only computer).  Xorg is your "window manager" in fact, this program is the first thing that you must load in order to be able to use your GUI (graphical user interface, your "windows").  When there is a problem with this software, be it drivers, hardware, whatever.  you usually can fall back into a "safe" text only mode.  now, if you tell me what I asked, I can try to help you.  otherwise, you have wasted my time.

---

### Post by Timothy Benton on 2007-10-16
i was wrong, i cant get into the command terminal. it started to run but then the screen got all messed up. but thanks for helping at least i know what is wrong now. heres my specs if thats what you meant by giving info:

Pentium M 1.5GHz
512MB RAM
Intel Mobile GMA 950

edit: haha you sound like my dad or something, "you have wasted my time."

---

### Post by travm on 2007-10-16
I assure you, I am not your dad.
does grub load at boot?

---

### Post by Timothy Benton on 2007-10-16
no. it either says "Boot Device Not Ready" because the hdd is empty or goes straight back to "install in text mode"

---

### Post by travm on 2007-10-16
ok, then you should install in text mode, have you done that before?  It is quite straight forward.

its suprising you are having video issues, my guess would be it is related to beryl/compiz effects being enabled by default in gutsy.  they are still ironing out the issues with that it seems.  I havnt got to try it yet (i only have dial up so to hell with downloading a testing release).  I think if you could get it installed and get into the recovery console we could get it fixed up for you.

---

### Post by travm on 2007-10-16
anyway im gone to bed, good luck, if you can get into recovery console, i would try after your text only install, your first boot, press esc when grub loads, select the recovery console entry, then you should be able to find some help on disabling the fancy effects from console, or fixing up your drivers.  maybe try selecting the vesa driver on install, it has been helpful to me before (it is like generic vga in windows).

---

### Post by Timothy Benton on 2007-10-17
Thanks! You were a great help. I'm running Ubuntu 7.10 now! All I had to do was use the Alternate CD and set the VGA mode to 640x480x16. If you didn't tell me it was a graphics problem I wouldn't have thought to try that. Also, with Feisty Fawn I needed ndiswrapper for my wireless. Not in Gutsy.

---

