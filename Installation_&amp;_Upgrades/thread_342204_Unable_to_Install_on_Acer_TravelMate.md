---
title: "Unable to Install on Acer TravelMate"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by DonBach on 2007-01-19
Hi!  I have an Acer TravelMate 2303LCi, 1.5 GHz Celeron M 340, 256 MB DDR.  When I look at RAM capacity, I see 240 MB and I think that video memory is gobbling some of this up.

The UBUNTU 6.06 LTS CD checks okay, but runs extremely slow off of the CD and hangs up if I ask it to install.  I downloaded and burned a new CD and it does the same thing.

I downloaded and burned UBUNTU 6.10 and it refuses to do anything.

I downloaded and burned XUBUNTU 6.06.1 and it hangs at the 56% loading Linux level.

Any suggestions?

Don

---

### Post by mkoyle on 2007-01-19
The most likely cause of this is ACPI support.  One long shot is that if you take out the battery and run on the charger, it will work.  When booting, try adding hpet=disable to the boot command.  If that doesn't do it, look around for information about noapic, nolapic, and acpi=off.  The good news is that one of these will probably fix the problem.  The bad news is that your battery life will probably be a little short.

You can also search the forums for acpi and see if you find anything related to your problem.

---

### Post by budgie9 on 2007-01-19
> **DonBach said:**
> Hi!  I have an Acer TravelMate 2303LCi, 1.5 GHz Celeron M 340, 256 MB DDR.  When I look at RAM capacity, I see 240 MB and I think that video memory is gobbling some of this up.

The UBUNTU 6.06 LTS CD checks okay, but runs extremely slow off of the CD and hangs up if I ask it to install.  I downloaded and burned a new CD and it does the same thing.

I downloaded and burned UBUNTU 6.10 and it refuses to do anything.

I downloaded and burned XUBUNTU 6.06.1 and it hangs at the 56% loading Linux level.

Any suggestions?

Don
I have that same model of of Acer, and mine installs and runs fine. No problems with either the Live cd or install. Strange one, I will be interested to hear how you get on.

---

