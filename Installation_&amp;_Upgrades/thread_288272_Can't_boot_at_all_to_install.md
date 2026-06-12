---
title: "Can't boot at all to install"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by jabzwnein on 2006-10-29
Can somebody explain what's going on with my computer?  I have downloaded the ubuntu iso at least five different times from five different servers and burned it onto ten different cd's using two different burn programs, yet I can't boot from the cd.  I get a screen "F1 to try again, F2 to enter setup menu".  I had a cd which worked once, but I wasn't able to boot from it again, and none of the other cd's every worked.  Please help!

---

### Post by DJ Wings on 2006-10-29
I have the same problem. Make sure that it boots from the CD before anything else (use the BIOS setup tool).

---

### Post by jd65pl on 2006-10-29
Have you tryed to run the disks in a different machine? Have you checked the MD5Sum of the downloads? It may be possible that  the cd drive is faulty or the brand of cds you are using aren't so good (i've had this many times!)

---

### Post by jabzwnein on 2006-10-30
Thanks for the advice.  I just tried one of the many CD's I made on another computer, and it worked fine, so it's obviously some kind of problem with my computer.  I changed the bios so it loads from the CD, but it still doesn't work.  Why isn't the computer reading the CD properly?  I first tried changing the boot order, so it started with the CD and then tried the hard-drive, but this didn't work - it just loaded Windows XP.  Then I shut off the floppy and hard drives, and just left it to boot from the CD drive.  But this doesn't work.  For some reason the drive doesn't read the CD properly.  What else can I do?  Can I add something to the bios boot list?  Right now it gives me the options "floppy drive, hard-drive, IDE CD drive" or something like that.  What's the IDE?  Maybe this is part of the problem?

---

### Post by lazyart on 2006-10-30
IDE is the interface that the CD connects to the system.  You should have that set first in BIOS.

If you boot this particular machine into Windows, can it read the CD?  Do you have multiple CD/DVD drives (maybe it wants to boot from the other drive)?

What's the manufacturer/model computer you are using?

---

### Post by morpheus5 on 2006-10-30
you might have a faulty CDrom? If installing using the CD doesn't works, u might have to try copying the installation image to an external hard-drive and then install from the external hard drive, i dont know if it works or not, but theoritically, it should work.

---

### Post by pattymnaish on 2006-10-30
This happened to me when I accidentaly burned the ISO as a data file. Check that out. ;)

---

### Post by jabzwnein on 2006-10-30
Thanks for the suggestions.  Some more info:

I burned the ISO properly, hence it works on other computers, so I don't think that's the problem.  In Windows, the computer can sometimes read the CD, sometimes not.  I've put the CD in all the drives (well, the two CD drives I have) and it doesn't work in either.  I'm using a Dell running Windows XP with service pack 2.  I've set the bios to try the CD drive first, but this never works and it automatically goes to the hard drive to boot.  When I deselect everything but the CD drive, the computer just won't boot.

How do I go about booting from an external hard drive?

---

### Post by lazyart on 2006-10-30
Maybe burn the CD at a slower speed?  Or clean the drives??

---

### Post by jd65pl on 2006-10-31
I suggest you try using a different brand of CD's are you using cd-rw? It is best to use plain old CR-R's. Also have a look around for an ubuntu boot floppy that could solve your problem.

---

