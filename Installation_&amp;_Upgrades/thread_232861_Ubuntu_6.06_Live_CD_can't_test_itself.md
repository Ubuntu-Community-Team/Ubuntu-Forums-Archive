---
title: "Ubuntu 6.06 Live CD can't test itself"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by EnigmaTS on 2006-08-09
I have a Compaq ProLiant 1600 with Dual PII 450MHz processors, 512MB of RAM, and a SmartArray Raid card with a RAID-5 Array configured.

Currently, the ONLY thing on the RAID-5 Logical drive is the Compaq Diagnostics partition.

I have never used any form of Unix/Linux/Ubuntu before, so when I received my 6.06 CD in the mail, I inserted it into the CD drive, and powered up my empty machine, eager to install Ubuntu.

Imagine my surprise when I came back about 3 minutes later to see a Black Screen Of Death (BSOD).  All there was on this black screen was a Flashing cursor in the Top LH corner of the screen!

So, I powered the machine Off and On again, and didn't walk away this time.  At the Live CD's main menu, I interrupted the automatic install.  I read all the Help 'stuff', but was not much wiser.

There was the possibility I was having ACPI problems, so I went the the Compaq Configuration utility, and set ACPI to Disabled.  Then I rebooted the Live CD, but still no luck.

Next I tried the Command Line install using the command:
 live acpi=off

There are about 3 lines of text appear quickly on the screen, with what appears to be the Kernal being decompressed and loaded, then the BSOD occurs.

There is constant disk activity on the RAID-5 Array (Contains 5 SCSI drives), but after 30 minutes the BSOD is STILL there, and nothing has changed (All drive activity lights are still flashing), and nothing has appeared on the screen to change the BSOD to something more useful.

So, it occured to me that the CD might be faulty.  As I said above, it is brand new, and arrived in the post today.  So, I thought I would use the Test the CD option on the Main Menu that the Live CD displays.

Imagine my surprise when all I got was a BSOD trying to test the CD drive!  There is no activity light on the CD or anything.

So, it would appear that there is some fundamental issue with my hardware.  However, the odd thing is that when I purchased the device (Just recently), it had Ubuntu already running on it.

Since I didn't have a User ID or password, I thought the easiest thing was to zap everythuing and start again.  Not so!

So, can anyone give me a few hints on what Ubuntu is doing with all this disk activity that starts just after teh Kernal is loaded, but NOTHING else is displayed?

---

