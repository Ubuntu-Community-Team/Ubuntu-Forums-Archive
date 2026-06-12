---
title: "[SOLVED] 7.04 install, won't boot"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by misawa on 2007-11-09
The system:  [PowerSpec 4988]("http://www.powerspec.com/systems/archives/system_archive.phtml?selection=4988"), 2.66 GHz Celeron, 1GB RAM, 40 GB HDD, IDE, using on board video

The install:  7.04 Feisty, LiveCD, known good and (essentially) installed ok this time.  After the install, the system rebooted - all good.  I did some tinkering, opening this and that, and rebooted again - all good.  I connected it my router, verified I had net access (Google, Yahoo, etc.) and ran Update Manager (System>Administration).  It comes back with 130 MB of updates that would take a while, so I said OK and let it start it downloading.  

The problems:  I check on the system after about 30 minutes and realize I forgot to shut off the screensaver.  I shake the mouse and after about 10 seconds, it shows me the desktop.  The mouse pointer is jumping around, but the update manager still seems to be downloading okay.  Five minutes later, I notice that the download time is now unknown, and shortly after that (~30 sec?) I get an error message that it's timed out(?).  I select OK and it starts acting like it's going to install everything it was able to download.  I leave it be and come back in another 10 minutes, and it hasn't changed anything - mouse still stuck in "hourglass" type mode and I can't move it.  I let it go another hour - same thing.  I deduce it's locked up.

The real problem:  I shut the PC down (held power button in for 5 sec) and then try to boot it.  It gets to it's Intel screen and freezes.  I boot again, attempting to F9 in to the BIOS, but only the same Intel screen.  I unplug the hard drive and boot it, same problem.  CD and DVD drives won't open, so I can't try to boot from the disc.  

Any tips on what to try next?  I'll probably manually open the CD or DVD and put the disc in, but I'm not so sure that'll work - neither drive light ever comes on when I first power up.  It's almost acting like it's lost the BIOS??

---

### Post by Pumalite on 2007-11-09
If this is a Desktop, flash the BIOS, and start again.
With on board video, I'd install with the Alternate CD.

---

### Post by misawa on 2007-11-09
How?  No 3.5" floppy drive available.  Never done it before either, but will research it.

---

### Post by Pumalite on 2007-11-09
[http://www.devhardware.com/c/a/Hardware-Guides/Why-and-How-to-Flash-Your-BIOS/](http://www.devhardware.com/c/a/Hardware-Guides/Why-and-How-to-Flash-Your-BIOS/)

---

### Post by Herman on 2007-11-09
All those updates probably loaded into your RAM and now that your computer was shut down while the RAM is still loaded, it's made something like a log jam in your RAM modules. You need to remove power from your RAM so the RAM modules will 'forget' all those updates.
All you need to do is completely unplug your computer's power cords and then plug them in again and try again to boot up.
Try that, I think that should work.

Regards, Herman.

---

### Post by misawa on 2007-11-12
Unplugged the IDE cable to CD and DVD drives and the PC booted.  I thought I had set both to cable select, but when looking at it upside down I got things backwards.  Set both drives to CS and plugged it back in to the motherboard and all is well.  Not quite sure how I got it to boot the first time, though, but I've used the PC all weekend now, rebooting it several times without a problem.

Thanks for all the input.

---

