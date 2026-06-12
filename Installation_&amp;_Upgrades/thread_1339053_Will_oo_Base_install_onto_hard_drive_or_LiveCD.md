---
title: "Will oo Base install onto hard drive or LiveCD?"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by FredVanH on 2009-11-27
Hi.  I recently installed Ubuntu 9.10 and am using it via a Live CD.  I noticed that OpenOffice.org's "Base" database program is not one of the menu-offered options.  If I install it from the "Ubuntu Software Center" menu choice, will it install onto the CD or onto the hard drive?  If the latter, will I be be defeating the purpose of the LiveCD and so therefore should I just wait for Base until I later install Ubuntu to the hard drive?
Thanks,
Fred

---

### Post by prshah on 2009-11-27
> **FredVanH said:**
> using it via a Live CD.
should I just wait for Base until I later install Ubuntu to the hard drive?

ooBase is not included on the live CD due to space constraints. In a live system, there is no "real" filesystem; the entire filesystem is a "virtual" one in memory. As such, you will not be able to "install" ooBase in a live session.

So please install Ubuntu first, and then you can install ooBase.

---

### Post by FredVanH on 2009-11-27
Thanks, PRShah!  This brings up the question:  Yesterday I used OpenOffice.org's Writer program, which is included in the LiveCD, to create a document;  then saved it.  Today I ran Writer again and opened the document, which the Open dialog said was stored in a directory/folder named "Documents".  Was it (and its folder) located on the liveCD or on my hard drive?
Thanks,
Fred

---

### Post by snowpine on 2009-11-27
The Live CD does not install or save anything to a physical disk *unless you specifically instruct it to.* Otherwise, all settings you change, applications you install, or documents you create are lost when you power off the computer.

Physical disks may be accessed through the Places menu.

---

### Post by FredVanH on 2009-11-27
Thanks to you both!  Based on your advice, I powered down to see if the document I had created in LiveCD's OpenOffice.org Writer would still be there after I re-powered up.  As you predicted, it was not there.  Your help is appreciated.  This was another of those things I could have tested for instead of asking about;  but was afraid to for fear of fouling up my hard drive.  I'll be more bold in the future.
Thanks again,
Fred

---

### Post by efflandt on 2009-11-27
The only way the live CD would store persistent data (settings, files, added programs, etc.) is if you have a partition on, or mounted on, the PC formatted suitable for Linux with a volume label "casper-rw" (case sensitive) or a loop mountable file with that name.  That is basically how the live/install iso on bootable USB works.  The casper-rw file on the USB device is actually an ext3 filesystem that can be loop mounted, and that is saved on shutdown to save peristent data.

---

### Post by FredVanH on 2009-11-27
Thanks, efflandt!  Detail is good.  All 3 of you have contributed greatly to a beginner's knowledge of how these things work far beyond the problem at hand, which I am eating up and which you may be sure will be the basis for further explorations on my part.
Thanks,
Fred

---

