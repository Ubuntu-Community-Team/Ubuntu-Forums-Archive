---
title: "edubuntu LTSP chroot"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by dedavie on 2007-06-28
I just moved into a new home that has cat5 wired throughout the house and i wanted to use edubuntu's ltsp feature to set up thin clients in my guest bedrooms, kitchen, sittingroom etc.  I purchased a used Dell 1600sc that came with windows that worked perfectly (except i hate windows server).  What i want to do is a clean install on a 36 gig hd with no dual boot, just plane and simple.  Everything works fine with the installation until it gets to the "installing ltsp chroot" then sits at 50% for 5 minutes then automaticaly goes back to the menue.  I click on the installation for ltsp and it goes to 50% then quickly goes back to the menue.  My disk image matches with the check sum so i know it can't be a bad image.  Is this a comon problem?  

Specs: Dell 1600sc: single 2.4 xeon, 36gig ultra320, 512 mbs ram, 1 on board gig nic, 1 intel pro 1000mt dual port server adapter (pci),  cup holder.



Thanx

Don.

---

### Post by dbott67 on 2007-07-04
Which installation disk are you using: the classroom desktop CD (live) or the server installation CD?  I used the server installation CD on a P3-500 w/256 MB RAM & 6 GB hard drive last week without issues (although the installation did take a while... especially at the 'chroot' part).

You might also want to try re-burning the CD at a slower speed (4x or 8x).  Back in the 4.10 or 5.04 days, I burned an image that generated lots of errors and eventually crapped out on me when I tried installing from it.  Re-burning at 4x fixed my problems.

-Dave

---

### Post by dedavie on 2007-07-09
You might also want to try re-burning the CD at a slower speed (4x or 8x). Back in the 4.10 or 5.04 days, I burned an image that generated lots of errors and eventually crapped out on me when I tried installing from it. Re-burning at 4x fixed my problems.

I am using the Edubuntu Server Installation cd.  I reburned the cd, checked it and re installed, same thing :(.  I reburned it at 4x and still hangs on the chroot.

---

### Post by dbott67 on 2007-07-09
Not sure what to tell you.  I tried another install on a different machine at work and it also worked properly (a P4-1.7, 30 GB hard drive & 256 MB RAM).  I've also successfully installed it into VMWare for testing purposes.

The only other thing that I can think of is that there may be a problem with the cup holder... err, CD-ROM on the server or possibly some sort of hardware conflict that's causing it.  Big help, eh?

If you've got a spare CD-ROM you can swap out, I'd start there first.

-Dave

---

