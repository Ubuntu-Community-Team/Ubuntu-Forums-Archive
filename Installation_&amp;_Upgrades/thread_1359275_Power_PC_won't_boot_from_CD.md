---
title: "Power PC won't boot from CD"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by gentix on 2009-12-19
I have an old Power PC G4 733 MHz desktop that I'm trying to get Ubuntu on, and I'm having trouble getting it to boot from CDs. First, I tried to boot from an Ubutu 8.04 CD (I've used this CD on PCs before so I know it works, but I've never tried to install Linux on a Mac before) and I held down the C key and it did a little frowny face with a folder with a question mark in the middle blinking.  Then I tried a CD with the DBAN release for Macs (because I wasn't sure if Macs need something special to tell them to boot it or something) and that didn't work either.  Any ideas? 

Thanks!!

Gentix

---

### Post by jerrrys on 2009-12-20
so older pc will just not boot from cd.  some you have to go into bios and set it to boot from cd. if you can boot from usb you can also install from thumb drive...

---

### Post by gentix on 2009-12-20
Right. Technically I think that this G4 doesn't have a bios, but it has something like it.  I got the boot-n-nuke CD cd to boot by holding down OPTION, though.  But the 8.04, OpenSUSE 11.1 and Vector Linux 5.9 cds won't boot.  They just don't show up on the menu. 

The thing I'm wondering is why did DBANZ offer a separate live CD download for Macs and why is that the only live CD that's working and are the two connected? As in, am I just stupidly trying to boot the wrong release of thes OS's?  Should I be using a different one because its an OLD mac?

---

### Post by Cheesemill on 2009-12-20
You need to use the PowerPC version of Ubuntu which can be found here:
[http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)

It's 8.04 only I'm afraid because that was the last they made for the PowerPC architecture and even that isn't officially supported by Ubuntu.

Edit - Sorry, my mistake. Newer versions can be found here:
[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

---

### Post by mkvnmtr on 2009-12-20
Yes you need the powerpc disk to install. You might run in to some problems getting it to boot but the Apple forum has som experienced people that can help. When I was using my Mac I found that the minimal install disk for ppc always booted and then I installed from the command line. I believe 8.04 was the last one I used on a Mac.

---

