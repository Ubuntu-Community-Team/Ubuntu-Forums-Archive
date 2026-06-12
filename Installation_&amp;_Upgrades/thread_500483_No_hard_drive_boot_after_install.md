---
title: "No hard drive boot after install"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by megamanjay on 2007-07-13
I have an AMD K8 3400 Processor with 2Gigs of ram, the motherboard is made by  MSI. I installed ubuntu and after I run the install disc, I try to let it boot up for the first time and right after the verifying DMI pool it says

CD: 
BOOT DISK FAILURE: INSERT SYSTEM DISK AND PRESS ENTER.

So i put the live CD back in the drive.  It boots up to the ubuntu live CD. I can go into the home folder and in the places column to the left there is a place called File System. What should i do now, because no matter what i try i can not get this to work i would like to get away from vista before it gets on something i own. Sorry if this is in the wrong place.

---

### Post by megamanjay on 2007-07-13
For the record i even took the cd rom out of the boot order for a time or two and it still gave me the message.

---

### Post by bdtgp on 2007-07-14
I think either one of two things is happening:  

1.  Somehow GRUB didn't install correctly.

2.  Is this a new system?  I just built my system and it gave me that error when I had a bad memory chip.  I had to do a clean install with the bad chip out.  I then went and exchanged the chips and now it works fine.  If this is the case and you have two DIMMS, try reinstalling with one of the chips out and then the other.  Find out which one is bad.

If it's not those or if you don't want to do that then I hope there is another suggestion of what's wrong.  Good luck!

---

### Post by megamanjay on 2007-07-14
Did it recognize both chips in the memory test on boot? that is what it is doing here, i will try your suggestion, it is a plausable one since the heat sink i bought is so huge it comes extremely close to the dimm in slot 0, it may be  touching it. Thanks

---

### Post by megamanjay on 2007-07-14
For those who end up looking at this I solved the problem myself messing with the jumpers on the hard drive, just make sure you are on Cable select on the drive, and Auto on the Hard drive, I found that on an earlier thread. Now it boots up flawlessly and works great. :lolflag:

---

