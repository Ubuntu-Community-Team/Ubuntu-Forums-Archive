---
title: "Harddrive Recognition?"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by RenegadeGopher on 2008-02-13
Comp trying to set 7.10 (text-based) on:

1998Gateway
400mhz pentium2
192mb ram

3 harddrives, one maxtor 20gb, one western dig 20gb, and an old 10gb drive from an OEM comp

All 3 harddrives have power, each one has an IDE cable hooked up to it, (not sure about teh master/slave config in the back of them), howwweeever

during every installation "no disk drive found: select a driver?" , and i've tried multiple combinations of HOW i hooked up the IDE cables, no fix found, and there are so many drivers i'm clueless as to which one i might need.. 

i've tried "wd7000" with only the western digital hooked up, and that didn't work, otherwise, i'm just unsure altogether about how these drives will be recognized

---

### Post by Existentialist on 2008-02-13
In order for the drives to be properly recognized by BIOS, the jumpers will need to be set to the master slave settings for the IDE cable with 2 drives, or in cable select mode on both drives.  If it is a single drive on the cable set the drive to master.  You can go in to BIOS and see if the drives are being recognized properly.  It will probably list IDE channel 0 and 1 and auto-detect the master/slave drives based on your jumper settings.  If a drive isn't showing up you most likely need to recheck your cable and drive settings for the 3 hds and any cd drives hooked up.

---

### Post by Pumalite on 2008-02-13
Beyond that; with that amount of RAM you better go for this:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
(Alternate)

---

