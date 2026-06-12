---
title: "CD Drive not responding, old computer"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by unquenchablefire on 2007-03-17
Ok, here's the situation:

I have an obsolete computer that I've been trying to play around with for a while. It is an ancient eMachine, 333mhz proc, 128mb ram, 12 gigs harddrive (8 + 4). I ran DBAN on it, and so now it's a completely blank slate. The only problem is that it is not recognizing the optical drives that i added. The optical drive that it came with is toast, and so i put in a DVD ROM drive and a CDR drive from another dead computer (the drives work though). 

Basically, it refuses to boot off of anything but floppy. Is there any way i could get xUbuntu running on this thing? I have the CD, and i know xUbuntu runs on the machine.

---

### Post by louieb on 2007-03-17
I've had some luck getting  older PC's  to boot a CD by using the Smart boot manager. [Heres my SBM page]("http://louboldt.com/ilinuxsbm.htm")

---

### Post by unquenchablefire on 2007-03-20
Well, I got SBM working, but i still can't seem to boot off of CD. I know that the drives are powered because they eject and the disk spins up. Still no response from the computer though.

---

### Post by zvacet on 2007-03-20
Does this help
[http://ubuntuforums.org/showthread.php?t=246486&highlight=floppy+install]("http://ubuntuforums.org/showthread.php?t=246486&highlight=floppy+install")

---

### Post by wpshooter on 2007-03-20
> **unquenchablefire said:**
> Well, I got SBM working, but i still can't seem to boot off of CD. I know that the drives are powered because they eject and the disk spins up. Still no response from the computer though.

Are you saying the the CD-Rom drive can not be made the FIRST bootable device in the BIOS ?

---

### Post by K.Mandla on 2007-03-20
[LIST=1]
[*]I'd try pulling the DVD and leave in only the CDROM. 
[*]Make sure the cables are set with primary master to the hard drive and secondary master to the CDROM. Don't use cable select on the jumpers, if you can help it.
[*]Check the BIOS for drive options, and if you can, upgrade it to the newest version.
[*]As a last resort, pull a completely different CDROM from a machine you know is working, just to be sure.
[/LIST]
And at the risk of asking a stupid question, are you sure your CD is properly burned? By that I mean, have you used your Xubuntu CD on another machine before?

---

### Post by unquenchablefire on 2007-03-21
Ok, to clarify:
1. I know the CD and drive are not at fault because i used them to install Xubuntu previous to a harddrive wipe
2. I haven't even opened up the computer recently, so it's highly plausible that i need to mess with my CD jumpers
3. When i got SBM running, i tried booting off of every port, but it all said "no operating system found". There were no slots that said "CD-Rom" just "Removable" and "Harddisk". 

I am going to open up the computer pretty soon and poke around inside. It may also be a problem with drivers, although i know next to nothing about the subject.

I may also wind up reinstalling 98 for a bit just so i can get my CD drive recognized...

---

### Post by wpshooter on 2007-03-21
Sounds like this system may be too old.  If you can't get the BIOS updated so that CD-Rom is listed as a bootable device, I believe I would move on to better things.

Good luck.

---

