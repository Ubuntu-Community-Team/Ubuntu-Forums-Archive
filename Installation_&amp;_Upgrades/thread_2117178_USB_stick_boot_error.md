---
title: "USB stick boot error"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by manthony121 on 2013-02-17
I have a computer that is loaded with 12.04 LTS as its only OS.  The other day, it stopped booting.  When powered on, it gets to the BIOS splash screen, then goes dark, there is a brief activity from the HDD, then it cycles back to the BIOS splash screen.  So, I popped a 12.04 CD into the CD-ROM drive, and it boots that OK.  Then, I tried booting off a USB stick, loaded with 12.04, and that didn't work, either.  It passes the BIOS splash screen, then gives a black screen with "Boot error" in the upper left corner.  The same USB stick works fine on other computers.

I tried the HDD and USB stick on another box, and determined that the problem was with the HDD.  Box #2 booted from the USB just fine.  I ran "fsck" on each partition of the HDD, and they all showed no errors.  So, I used "boot-repair" on the HDD, and it is now working again.  However, trying to boot from the USB stick on Box #1 still gives the Boot error message.

I have seen people asking about the USB "Boot error" message in other threads, but I have not seen an answer for it.  Has anyone found the cause of that problem?  Is it unique to certain BIOSes?  It is entirely possible that Box #1 has never worked with a USB stick, and I just never had occasion to find out before now.


Here are the hardware specs:

MOBO: Intel D945GNT
CPU:  Pentium 4 CPU 3.00 GHz
BIOS date: 02/08/2006

---

### Post by presence1960 on 2013-02-17
Did you consider the bootable stick setup is bad? Try setting it up again and see if that works.

---

### Post by manthony121 on 2013-02-17
> **presence1960 said:**
> Did you consider the bootable stick setup is bad? Try setting it up again and see if that works.

The USB stick worked fine on two other boxes, so I'm pretty sure it's OK.

---

