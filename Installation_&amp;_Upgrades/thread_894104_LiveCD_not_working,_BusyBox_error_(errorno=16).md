---
title: "LiveCD not working, BusyBox error (errorno=16)"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by sexyclient on 2008-08-18
I'm trying to install 8.04.1 on my pc, but I keep running into the same problem and I just can't seem to get past it...  Machine specs (to the best of my knowledge) are as follows:

Sony VGC RB-30; 
Pentium4 3 ghz, 800mhz bus, 512 mb ram, Intel GMA 945;
SATA HD 180 gb with XP and a second boot partition for it; 
and a PATA supermulti drive with the dvd as the master and CD as the slave.

The problem is that after I select the option to boot the liveCD - actually, all of the options yields the same results, which is that - I get a black screen that has the following: 

BusyBox, SRST, ide1 and errorno=16

That isn't the exact message, rather snippets of a larger message that I'm unable to memorize - despite the hours I've encountered it while trying to circumvent its appearance.

Other key bits of info that may be of help are:
- I've run a liveCD from an older version of ubuntu before, and I had no problems.
- I'm fairly certain that the CD is without defects
- The alternate liveCD image causes the same problems *<-- edit*
- I've tried pressing F6 on the menu and typing "all_generic_ide floppy=off irqpoll" (without the quotes)
- I have no option in my BIOS menu to set the mode to RAID, or IDE, or to disable/enable floppy drive even though I don't have one

I've searched all over, and found and tried many different "solutions", but to no avail.  I've been trying for more than 5 hours to install hardy and I don't want to give up, but there doesn't appear to be any solution for this problem for me.  Can anyone provide some help?

:KS :popcorn: :guitar: :lolflag: :confused:

---

### Post by dstew on 2008-08-19
I assume that you did the CD integrity check, or have tested this same CD and found that it boots fine in another computer.

This type of error (dropping to BusyBox) usually means the Live CD Linux kernel is not able to operate with your hardware. There are other kernel parameters to try, like **acpi=off**, **noapic**, **nolapic**. If you still can't get it to work, try a different linux distribution, or install an older Ubuntu with a different kernel. Sometimes, if you can get an older Ubuntu to work, you can then upgrade to 8.04 online, without using a CD.

---

### Post by sexyclient on 2008-08-19
tee hee...

Actually I didn't realize the machine had two removable media drives: the supermulti drive, and another cd-rom drive.  My problem was solved after installing from the cd-rom drive!

My condolences to those of you who are experiencing the same problem and are fairly sure you don't have a second removable media drive that you're overlooking.

---

