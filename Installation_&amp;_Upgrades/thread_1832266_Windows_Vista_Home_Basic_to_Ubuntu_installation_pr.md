---
title: "Windows Vista Home Basic to Ubuntu installation problem"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by MSTRZ on 2011-08-24
********READ SECOND POST**********









Hello, MSTRZ here. For a VERY long time, I have wanted Ubuntu. I have tried numerous times on numerous dates to install Ubuntu. I have solved numerous problems, but still, one problem seems to daunt me.

My system specs are:

Computer Type - Laptop
Operating System - Microsoft Windows Vista Home Basic Edition
Manufactured by -  Gateway
Model Number - ML3109
Processor - Intel Celeron M CPU     520 @ 1.60Ghz
Memory (RAM) - 2014MB
System type - 32-bit operating system
Graphics - ATI Radeon XPRESS 200M Series




My problem is:

With the LiveCD installation:
I edited the BIOS settings to boot directly from the CD, I know I did this correctly.
Whenever I boot via the LiveCD, the purple Ubuntu boot screen displays. It will hang there for about 5 minutes, then transition to a black screen with a blinking underscore.
 
this ---> _

It will hang there for 10-20 minutes, sometimes changing resoloutions, at which point I start to get annoyed and restart the system, booting back into Windows to look at some tutorials, or try something else, etc.

I solved THIS by holding down the SHIFT key BEFORE the purple boot screen came up. Doing this launched me directly into the big Ubuntu screen, with the options:
"Try Ubuntu without installing"
"Install Ubuntu"
"Check Disc For Errors"
And so on, and so forth.

Okay, this is good, so I navigate up to the "Install Ubuntu" option and press enter. The black screen appears, but still has the blinking underscore on it. Nothing more.

End of first problem.

My problem:
With the Wubi installer:

I download Wubi from your website, run it, install Ubuntu, with the lowercase username, passwords, everything I need to do.
I re-boot my computer to finish the install, then quickly check in the C drive to make sure the installed Wubi/Ubuntu folders are there. I browse through them, yep, everything installed correctly.

I shutdown my computer, and re-boot it again. This time it gives me an interface:
"Choose which operating system to boot"
Or something to that effect, I'm writing this from memory...

Underneath that are two options:

Windows Vista Home Basic
and
Ubuntu

Okay, great, I can boot up Ubuntu now.

I navigate to the Ubuntu button and hit enter.

Still, that stupid black screen with the blinking underscore!!!

Okay, okay, let's try to boot Ubuntu from Wubi in SAFE MODE.

That's the ONLY thing I could POSSIBLY think of at this stage.

I boot Ubuntu up in safe mode, okay, looks good, my screen is filled with command line dailouge, Ubuntu seems to be running tests of some sort...Then it freezes up, right after the line about some program, with some guy's name...Paul Azawkowich or something like that.

Okay, now I'm offically stumped. I turn to the forums for help.
Please respond if you can.
Thanks,
           MSTRZ









**********READ SECOND POST**********

---

### Post by MSTRZ on 2011-08-24
Okay, I got Ubuntu installed! Yay, applause, tears of happiness, etc.
Now, whenever I try to boot it up, it just hangs at the purple boot screen!!
What do I do, please help???

---

### Post by 8jwong14 on 2011-08-24
> **MSTRZ said:**
> Okay, I got Ubuntu installed! Yay, applause, tears of happiness, etc.
Now, whenever I try to boot it up, it just hangs at the purple boot screen!!
What do I do, please help???
That's interesting.  On my laptop, this problem happened to me with Ubuntu 11.04.  But worked fine with 10.04.  What version of Ubuntu are you installing?

---

### Post by MSTRZ on 2011-08-25
11.04, that latest version. it seemed to succeed with a combo of LiveCD  and Wubi. I installed Wubi, then booted up the LiveCD and Ubuntu  installed fine, all except for the purple screen of death, I guess you  could call it.
I suppose I could try Shift>F6 to bring up the  advanced GRUB menu, and boot up with those two options disabled, the  ones that seem to be causing everyone a lot of problems, but I haven't  tried it yet.

Sorry about the late reply, I had to go out to my  brother's gymnastics meeting, then after we got home, I had to help  prepare for the hurricane that just might graze us...I hope you're still  willing to help me! :(

---

