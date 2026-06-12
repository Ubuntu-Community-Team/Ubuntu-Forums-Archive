---
title: "How to set up two versions of Ubuntu?"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by owlcroft on 2010-11-24
At present, I have two drives connected, a 250-GB SATA, on which I have Ubuntu upgraded to 10.04 with what I guess is GRUB1, and the other an 80-GB SCSI drive on which at present I have a non-Linux system (OS/2).  My GRUB menu has, at the bottom, this set of lines (which work fine to add OS/2 as a functional boot-menu entry):
```
title           OS/2 Boot Manager
root            (hd1,3)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```
What I now want to do is use that second drive to do a clean test-install of 10.10 from CD (wiping the drive clean).  What I am asking is how do I go about that so that the new install:

a) ends up on that drive, and does not interfere with my current setup on the first drive; and 

b) gets an entry in the displayed boot menu?

My best guess is that I would hand-edit the GRUB lines cited above (before even doing the 10.10 install) to be--
```
title		Ubuntu Maverick 10.10
root		(hd1)
chainloader	+1
```
--but I'd like to be very, very sure.  I also assume--ever-dangerous word!--that the easy way (or at any rate the safest way) to do the 10.10 install is to power-down, unplug the SATA drive, then power back up and boot from the install CD.  Would that leave the 10.10 install OK after I re-connect the SATA drive?  (That is, does anything get confused if the "identity" of the drive changes after the install?)

I want these two systems to be completely independent--that is, I do not need either to have access to the other's drive and files (and in fact it would be better if neither, when running, is even aware of the other).

---

### Post by owlcroft on 2010-11-26
Does *no one* here have any help to offer?

---

