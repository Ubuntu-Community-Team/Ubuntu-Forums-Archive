---
title: "Switching hard drives question"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by krumble on 2007-08-05
Well, I just bought a new hard drive because my 40gig was way too small for my music.  I was gonna install it and just use the 40 gig for my windows and ubuntu OS, but I realized that my computer doesn't support 2 hard drives.  I was wondering if there is a way that I could make like a back up of my ubuntu system files onto a cd then use that to install ubuntu on the new hard drive.

---

### Post by Pumalite on 2007-08-05
Use AptON CD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by talby on 2007-08-05
If you have a CDROM drive are you able to remove it temporarily to install the second hdd?

If so, you can do that then clone your current hdd to the new one using ghost (or ntfsprogs) to clone the ntfs partition and you can manually clone the linux install or use something like partimage.  I believe ntfsprogs (aka ntfstools) and partimage are available in universe repos.

---

### Post by krumble on 2007-08-05
I think i might be able to put second hard drive in because theres another slot on my mother board and i have a blank space to hold a floppy which I don't have.  I think it will fit there.  Another question though, which one do i plug it in to, theres only 2 that will fit which is P3 and P4

---

### Post by fredj on 2007-08-05
krumble
You are really being challenged here because you don't have a clue about hardware do you?
Open your computer and look at the cable that goes to you hard drive. Is it a wide ribbon cable,
if so you have an IDE drive system. Does the cable have a spare drive connector on it.
If so set the jumpers on your new drive to the SLAVE position, install it and plug it into the drive
ribbon cable and the power supply.

If your drives don't have a wide ribbon cable then they are SATA drives, so install it, connect a 
power cable and a SATA cable and that is it. You will need to Partition and Format the drive.
Good luck!

---

### Post by krumble on 2007-08-06
:-k umm sure, well I know it is an SATA, but I dont have another connector thingy for the power to plug it in my hard drive. But I'm gonna go to radio shack or circuit city to see if they have one.  Ill post where I'm at tomorrow. Thanks for the help

---

