---
title: "problems getting install to start"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by harbingerofdoom on 2010-11-04
i have a dell 2400 that i had installed xubuntu on with no issues. I tried to install a geforce fx5200 which to make a long story short, pretty much hosed the entire OS.

So i went to reinstall, and upon doing so, first i was unable to boot from the disk, i thought perhaps a power issue may be at play (the stock power supply is only 200watts max) so i tossed in a 600 watt PSU, that seemed to get the issue with being able to boot from the CD corrected but now im at a situation where it boots to the menu (try without disturbing your current OS, install, mem test or CPU test) then i get the language selection. pick english, select install and it all stops right there.

im really not sure whats going on with this issue. could it possibly be that its seeing an existing linux partition and refusing to go any further? (if so that wont be a problem tomorrow, im installing XP on it right now which was just a test to rule out hardware issues... so far its installing with no issues)

last note is that after trying to boot from an arch distro disk and an ubuntu disk, i got the ubuntu splash screen back, but its really messed up and the progress bars are all just large blocks and it was dying there when booting off the HDD.

ive never run across a situation like this when installing linux before so im not sure which way to go with it.

---

### Post by harbingerofdoom on 2010-11-04
anyone?

---

### Post by harbingerofdoom on 2010-11-05
help?

---

### Post by P4man on 2010-11-05
Try booting with nomodeset. See my signature.

---

### Post by harbingerofdoom on 2010-11-06
> **P4man said:**
> Try booting with nomodeset. See my signature.
 
 
tried, but that did the same thing.
 
2 additional notes:
 
the only difference in the hardware is the fx5200 xubuntu was running on this using the onboard intel graphics driver to begin with. so the likelihood that its anything other than the video card is low. this is also an fx5200 PCI...its not AGP.
 
I found an xbmc live disk and tried to boot off of that just to see what was going on, it also will not start up using the nvidia drivers and when selecting safemode with nvidia drivers, it gets to 'loading drivers' and just hangs.. the cursor still spins, just nothing ever happens after that.

---

