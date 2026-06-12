---
title: "Problem - SATA Drive was there, now it Isn't"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by Saethan on 2008-06-11
I'm attempting to install 8.04 on a computer with an ASUS P5N-D motherboard, and a WD 250gb SATA hard drive.

Here's what happened..

I put everything together, set up the BIOS, it recognized everything correctly(first try, I knew it was too easy...), popped in the live CD and began installing.

Got to the partitioner, it found the WD SATA drive, I went with the defaults, and it started partitioning.  Then I got an error saying it was unable to partition the drive(wish I remember the exact error), and returned me to the partition screen.  I tried a couple more times, got the same error, then exited the installer and restarted the computer.

Then BIOS pops up... and it no longer finds the WD drive.  It just has a blank in the POST screen where the WD drive used to be listed.  The SATA DVD drive still works fine.

Things I've tried so far:
replaced the SATA cable(twice)
moved the SATA cable to two different ports
moved the drive onto a different power cable
reran the setup - didn't find any drives

It's kind of frustrating, do you guys think maybe the HDD died?  I can't think of what else might have happened.

Anybody have any ideas?

---

### Post by Saethan on 2008-06-11
One more detail - the BIOS knows that -something- is there, since under SATA1 it has a blank, instead of saying [none] like it does under SATA2 & 3

Also, when going into the boot order it lists SATA1 as a hard disk, though that might just be default for when it doesn't know what it is.

---

### Post by Pumalite on 2008-06-11
Check your drive with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

