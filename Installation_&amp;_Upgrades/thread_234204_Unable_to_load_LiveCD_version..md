---
title: "Unable to load LiveCD version."
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by pockey on 2006-08-11
I downloaded the ISO for Ubuntu from the official site, and burned the ISO, as an iso, to a CD.

The site said most ISOs are around 700MB, and when I downloaded this it said 658MB but once finished, it was only 334MB. I burned it anyway, and rebooted my computer. I set my primary boot to my disk drive, after inserting my disk, and when I reboot it just goes straight to Windows.

I'd like to try Ubuntu from a LiveCD before creating a new partition for it. What am I doing wrong?

Thanks for any help!

---

### Post by jordilin on 2006-08-11
> **pockey said:**
> I downloaded the ISO for Ubuntu from the official site, and burned the ISO, as an iso, to a CD.

The site said most ISOs are around 700MB, and when I downloaded this it said 658MB but once finished, it was only 334MB. 


No, it should be around 700MB, so something must be wrong

> I burned it anyway, and rebooted my computer. I set my primary boot to my disk drive, after inserting my disk, and when I reboot it just goes straight to Windows.

Change the parameter BIOS to boot first from CD

---

### Post by pockey on 2006-08-11
Okay, I downloaded the torrent instead this time and burned it to another disk, and it works now. When I reboot, it loads Ubuntu.

However, when it comes up it goes to a screen with a loading bar and says "Mounting root file" or something close to that, and hung there for a very long time so I pressed enter and escape just to see if anything would happen and it took me to a black screen telling me the drive isn't ready for the command or something.


Soooo yeah, I have no idea what I'm doing. :-k

---

### Post by jordilin on 2006-08-11
> **pockey said:**
> Okay, I downloaded the torrent instead this time and burned it to another disk, and it works now. When I reboot, it loads Ubuntu.

However, when it comes up it goes to a screen with a loading bar and says "Mounting root file" or something close to that, and hung there for a very long time so I pressed enter and escape just to see if anything would happen and it took me to a black screen telling me the drive isn't ready for the command or something.


Soooo yeah, I have no idea what I'm doing. :-k

"Mounting file root" takes a while, but not a lot.

---

### Post by pockey on 2006-08-11
I just rebooted again, and mounting the root file didn't take as long this time, but it still takes me to the same black screen afterwards.

The black screen says:

Timeout waiting for DMA
Drive not ready for command

and waits for me to type something.

---

### Post by jordilin on 2006-08-11
I would take a look at the computer BIOS and check its parameters.

---

