---
title: "CRC Error after BIOS upgrade"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by JordanH on 2007-06-04
Hi All,

The short story...
I just upgraded my BIOS on my AMD1.4GHz machine with the intention to install Ubuntu 7.0.4 fresh off the CD onto an empty hard drive.  The machine begins to boot off of the CD but after I choose the option to run or install Ubuntu, the system hangs with the error "CRC Error  -- System Halted".

Typically, I would suspect this is a problem reading from the CD-ROM drive, however, it happens on both CD-ROM drives now where prior to the BIOS upgrade it did not.

I'm at a loss for how to work around this problem.  Any ideas?

The long story...
My old 1.4GHz box is about to take on a second life.  An upgrade from Ubuntu 6.0.6 on a 20GB drive to a fresh install of Ubuntu 7.0.4 on a 160GB drive plus raided 2xSata 320GB drives for data.  No problem right?
1.  I verify that I can boot off of the CD-ROM drive into a Live session of 7.0.4 - no problems.
2.  I swap out the 20GB drive for the 160GB drive and install Ubuntu on the 160GB drive.
3.  I boot the system for the "first" time and receie errors errors that the HD is larger than the bios can bare.
4.  I upgrade to the latest version of the bios without problems.
5.  I try to boot but the system tells me it can't find the drive.  Perhaps I gummed up the Grub install??
6.  I try to boot from the CD-ROM but I get a CRC Error after the CD tries to start a Live session.
7.  I try to boot from the DVD-ROM but I get a CRC Error after the CD tries to start a live session.

Here I sit with a system that won't boot from HD or other source.
If I revert to an older BIOS, I can't use my HD's.  If I keep the current level of BIOS, I can't use the system.

Any suggestions?

J.

---

