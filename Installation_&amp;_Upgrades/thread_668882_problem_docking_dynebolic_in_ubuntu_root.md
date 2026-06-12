---
title: "problem docking dynebolic in ubuntu root?"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by chaparrazo on 2008-01-15
I have a PIII box with 256MB mem with ubuntu 7.10 on  it. I burned the latest dyne:bolic CD and have it docked on two other windoze computers (Dell PIV and Dell centrino laptop) and running great. This is a cool setup! 

It seems the CD is not reading well on the old box so some of the module files didn't copy over well. So I've tried to copy the module files over using a USB stick and they seem to be fine. I used 

alt-f2 and gksudo nautilus

to copy the files into the root. Every time I try to boot with the dyne CD it ends in text mode only with an error saying something about the file xorg.dyne

A few questions: am I supposed to copy the dyne into the root or into home? 

Any other ideas why it's funking out? 

Thanks for your help!

---

### Post by tgalati4 on 2008-01-16
Older CD ROM drives sometimes have problems with newer burned disks.  Try reburning dynebolic using different media and burning at 4X speed.

Look for a newer CD drive to put in the second bay of the PIII machine.  You shouldn't need to copy any files over.  Dynebolic loads and runs off of the CD.  Only the nest files really need to be copied, and that occurs automatically once it is set up.

If you want dynebolic permanently installed, you need to copy the dyne directory and I believe the live CD will read that directory and boot from it.  But if your CD drive is wonky, then I would  not expect all the files to be correctly copied anyway.

You might get a USB flash drive and copy the ISO to it.  See if your BIOS will allow boot from USB.  If not, then create a USB boot floppy.  This is a floppy that will boot a mini shell which will then load the drivers necessary to boot off of the USB.  Search the forums for links to a USB boot floppy.

---

