---
title: "Installing on a G3"
date: 2005-09-09
forum: Installation &amp; Upgrades
---

### Post by John Azelvandre on 2005-09-09
I am attempting to install ubuntu (Hoary) on a Mac G3.  The first hurdle I encounter is early.  After it says it is loading the kernel, a message comes up that says:

H. V frequency over range,

Then the machine goes into "Off Mode."

That's as far as I get.  I attempted a default install.  

What this mean?  I don't know much about PowerPC hardware ...

Thanks in advance,
John

---

### Post by DJ_Max on 2005-09-09
First of all, what do you mean by Mac G3? iBook, PowerBook, iMac, PowerMac, etc..

Second, what do you mean by "off mode"?

---

### Post by John Azelvandre on 2005-09-09
Thanks for your response,

What I meant by "off mode" is that a message saying "off mode in 5 seconds" or something like that appears on screen and the unit turns off. (and thus the install fails.)

Let me preface this by saying that I neither like nor have much experience with Mac hardware.  I've successfully installed and run Debian Sarge for the past year on my PC at home; now I thought I would try putting Ubuntu on an old Mac I have a work.  I'm a school teacher.

This is a blue and white G3 desktop computer.  Probably an iMac or PowerMac?  It is a blue and white tower with separate monitor and keyboard.  It isn't a laptop and it isn't one of those all in one monitor/cpu units.  That is the extent of my knowledge about Macs.

After I posted that message, I tried running the install with the option 'video=ofonly.' That has seemed to work.  I haven't fully completed the install yet; it's at work, I'm at home now.  I left it unpacking packages.  Couldn't stay around.  So when I go back I'll see where I'm at.  I suspect that something about the monitor or video driver didn't agree with the default install program.  So, I'll probably be trouble-shooting GUI setup ... more to come!

---

### Post by DJ_Max on 2005-09-09
It's more than likely a early model PoweMac. All iMacs have integrated monitors. I have always had issues with GUI during installs with other distro's. But X11 has always been setup correctly. Ubuntu pretty much as a standard curses installer.

You may or may not have issues with GUI setup for your desktop.

BTW, is this your Mac? [http://lowendmac.com/ppc/g3c.shtml](http://lowendmac.com/ppc/g3c.shtml)

---

### Post by John Azelvandre on 2005-09-14
Yes, that's my Mac!  It has 128M of Ram, and the Rage Pro video card.  I'm still having xserver issues -- see my other post.  Otherwise, if all I wanted was command-line linux, it would be working fine.  I'm not sure if the video driver is "Rev.1" or Rev.2, that might be part of the problem.

---

### Post by Ocyberbum on 2005-11-04
I have a similar question?:confused: 

I just got a laptop, mac, powerbook g3 series <black> with mac 9.1 and no restore cd's. And I want to put Ubuntu on it as well but I can’t get mine to pick up the Cd and boot? I have tried holding down the "c" key and option-shift-delete but with no luck.....i was hoping one of you could give me a hand.....

thanks in advance
Billy

---

### Post by jmdennis on 2005-11-30
I am having problems installing on my blue and white as well.  It mainly dies just before it actually does any of the install.  It finds every thing but then just halts.  I have gotten it to start doing the load but dies on the cd drive.  I am going to try and replace this today to see if this helps.  For me it gets to different places every time I turn the pc off and then back on but not far enough to get to use this.  I have been able to load OS 9 on it just fine and it has all the firmware updates done.  I know that the disc's are fine that I burned.  I am also getting a yellow dog linux cd as well and will try this out to see if it works on my machine.

---

### Post by jmdennis on 2005-12-02
I tried to replace the cd drive but the same problems as before.  I got it to detect the hardware and so far it is stuck on 2% trying to find the cd-rom drives which I only have one.  I have had this get up to 26% but then it stops.  I can leave it for hours like this and it does not get any further.  I have tried all the install commands that I know to try and get this to install but so far no luck.

---

