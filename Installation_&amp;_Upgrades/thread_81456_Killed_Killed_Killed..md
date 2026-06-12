---
title: "Killed Killed Killed."
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by Zachary on 2005-10-24
Hey fellow Ubuntu Users :)

I've been trying to install Ubuntu Breezy Badger for sometime now and I cannot get it installed. I get halted by the same error each time I try. I hope that maybe with luck there is someone that can help me, thanks and I will really appreciate it if you can.

After selecting language, location, entering my host name, detecting disks and hardware and then when it's just about to install the base system I get a screen fulled with this :

Killed
Killed
Killed
Killed
Killed

That starts at the bottom and with a 1 second interval the 'Killed' eventually fulls my entire monitor screen, from bottom to top.
If there is anyone that could tell me in the least what this could mean I would really be thankful.

This machine that I'm currently trying to install Ubuntu Breezy Badger on was running Ubuntu Hoary Hedgehog before perfectly fine, so I don't really know what the problem could be.

Here's the specifications of the machine :
Pentuim-MMX 266 Mhz 
On-Board graphics
64 MB RAM
2 GB HDD

And oh yes, I want to install the Ubuntu Breezy Badger server and I've also tried all the other options, desktop etc. I've also tried writing the cd again and I've checked the MD5SUMS of the downloaded ISO.

I hope that that information helps in anyway possible.

Thanks once again in advance.
Zac

---

### Post by ubuntu27 on 2005-10-24
WoW I enver had that kind of problem...

I think it is better to upgrade to Breezy with a Clean install and not "distro-update" That way you will have less problem.

Did you try yo upgrade your distro using the Terminal ?
Try installing using the CD.

---

### Post by Zachary on 2005-10-24
Hey thanks for replying. :)

I have downloaded the Breezy Badger ISO and I've written it to cd. That's where I'm trying to install from.

---

### Post by az on 2005-10-24
CTRL-ALT-F3, and that brings you to the error console.  It is more verbose than what you are seeing.  What is displayed?

Can you CTRL-ALt-F2 into a terminal?  You can check (and save) the logs from there.

---

### Post by Zachary on 2005-10-24
thanks, I tried CTRL-ALT-F3 and this is what I got, there's a screen full of :

'insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/pci/' 
followed by a bunch of files listed, I will write out the last 3 just incase the problem is there:

insmod /lib/modules/2.6.12-9-386/kernel/drivers/cdrom/cdrom.ko
insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-cd.ko
insmod /lib/modules/2.6.12-9-386/kernel/fs/isofs/isofs.ko

and that's where it ends. 
does that help at all?

---

### Post by taurus on 2005-10-24
Looks like there is a problem with your CD-ROM!!!  What kind of CD drive is it and how does it connect to your computer???

---

### Post by az on 2005-10-25
Those are normal messages.  They are not errors.

You will have to go into the second terminal (F2) and open up the log files to see exactly what is going on.  I cannot tell you what log to look at, you will have to look at all of them.  Is your keybord frozen when it displays (killed....)?

---

### Post by flower on 2005-10-25
try to go to console #2 and do `ps ax`
see if the installation will continue if you kill 1-2 of the last created processes :)
that worked for me 

p.s. after I did the install I found 8G error log file in /var/log (so ... you can check it if killing the stuck process worked for you)

---

