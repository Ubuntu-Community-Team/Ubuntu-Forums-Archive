---
title: "Installing 8.10 on a new partition (It broke)"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by gigatwo on 2008-12-01
Amd64 Anthlon 3200+
1 gig ram (DDR I believe)
Gforce 7600 GT (PCI express)
MAXTOR 250 ish GB hard drive
(Motherboard has a nvidia chipset)

Basically, I'm trying to install 8.10 (*32 bit for stability*) on a partition through the live cd. I've tried multiple times, and about halfway through the install my display goes to a console or BIOS setup. After a bit of time a blue screen pops up saying that the Gnome Display manager shut down and that it'll try to re-open in 6 minutes. When I press "ok" it goes back to the console screen and 6 minutes later the message comes up again. How do I work around this error. Should I try installing without the live CD gui? If so, how do I do that?

It's also probably important to note that the hard drive Does get partitioned. The OS just isn't on it.

---

### Post by lemming465 on 2008-12-03
Are there any other OS's on this box, and if so, do they work?
If you boot the live CD, can you run it for an hour without problems?
Can you run the installer in "safe" graphics mode?

A couple of possible things you could try related to hardware issues.  Run memtest86+ for about 20 minutes to verify you don't have bad RAM.  Run the CD verify to check that you don't have a bad burn.  If the BIOS has a CPU temperature display, find out if your CPU is overheating.  If it doesn't, at least check that your fans are all working.  If you have a voltmeter, or can borrow one, check that your power supply is producing appropriate 5v and 12v outputs.

---

