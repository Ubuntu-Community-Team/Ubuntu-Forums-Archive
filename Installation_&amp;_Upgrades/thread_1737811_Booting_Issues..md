---
title: "Booting Issues."
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Beryllium on 2011-04-23
This was copied straight out of another forum which I purposed my problem. I thought there would be more expertise here who could tell me the cause of my booting problem.

> I'm having issues loading an operating system onto a computer. I've tried to put both MS Windows XP and Ubuntu 10.10 with no success.

My computer hardware, if it helps:
Motherboard - K7VTA3 / KT333 (printed on the board, may not be correct) with AwardBIOS
AMD Athlon XP 2100
ATI Radeon 9800 XT (128 MB)
512 MB DDR RAM
40 GB HDD

First I put my Win XP disc into my computer and it booted up, but gave me an error before I get to the "Repair/Install/Exit" screen. I tried a bunch of different disc drives but none helped. It does not give me the same error every time.

I quickly gave up on installing XP and moved onto Ubuntu.

The first time I put my Ubuntu 10.10 disc into the drive it booted up slowly, up to the "Try/Install" screen. I clicked install and cursor changed to show it was loading but absolutely nothing happen for 20 minutes, with is when I gave up and reset the computer. The second time around it did not get past the purple screen with the weird symbol and the stickman. It does not get to the screen with the Ubuntu logo and loading dots thing. I mucked around with the BIOS settings, noe help (they are not back at their defaults). I also tried an USB installer. The BIOS couldn't boot it.

I tried the minimal CD with the intention of installing Ubuntu from the internet but this boots into an everlasting black screen.

I tried a bunch of different discs and drives but none get past this screen anymore. So I tried some more exotic ways of installing Ubuntu, none of which were ever going to work, but worth a try:

First I took the hard disc out and put in in another computer, and used Wubi to install Ubuntu to the hard disk. I put it back in the computer and it gave me

[QUOTE]ERROR LOADING OPERATING SYSTEM INSERT SYSTEM DISC AND PRESS ENTER

Then I put the hard disk back in the other computer and installed it again, but this time using the live CD. I put it back and this time it give me something like
Quote
> Invalid partition table blah blah blah
Then the Grub command line. This is the current state of the computer.

So my remaining options are:
Do something from Grub
Boot over network

If you can magically reinstall Ubuntu from grub, that'd be great (but probably unlikely)
Else would someone give me a complete idiots guide to set up network booting?

EDIT: My research tells me grub is only a bootloader. Damn.[/QUOTE]

Thank you.

---

### Post by mörgæs on 2011-04-24
If you erase the disk completely with Killdisk as explained here
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)
do you get any error messages?

---

### Post by Beryllium on 2011-04-24
But even if the hard disk is bad it should still boot the disc CD right? And have taken the hard disk out and it still won't boot into anything useful.

---

### Post by Hedgehog1 on 2011-04-25
> **Beryllium said:**
> But even if the hard disk is bad it should still boot the disc CD right? And have taken the hard disk out and it still won't boot into anything useful.

Right now, based on what I read from you post, you have one of two conditions:

* Bad CD Drive

* Bad Drive Controller (controls the CD Drive and the Hard Disks)

The greatest likelihood is that the CD drive is bad (they wear out over time).

Are the CD Drive and Hard Disk both IDE on this system?  If so, scrounging a used IDE CD Drive is very possible as most computer folks have a few in the closet.

In any case, borrow a CD drive and try installing again.

***The Hedge***

:KS

---

