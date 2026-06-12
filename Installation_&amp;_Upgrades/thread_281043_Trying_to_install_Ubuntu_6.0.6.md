---
title: "Trying to install Ubuntu 6.0.6"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by Davec1 on 2006-10-20
I have always wanted to try Linux, and Leo Laporte got me interested, so I am in the process of trying to install Ubuntu 6.0.6 but seem to be stuck. 
I D/Loaded the .iso file for i386 Desktop, and burned it to  a CD.
All appears to be ok.
When I boot, it boots from the CD and goes right to the options screen where I choose to Start.
It then goes to the screen with Ubuntu  symbol on top and below, it says.... Load essential Drivers.      OK
and ....Mount Root file system.
After that it freezes, and eventually I have to shut down.

When downloading the Ubuntu files there were so many I got a little confused, I wanted the one that runs from the CD without installing it.
I may have the wrong one here...
 Any help will be much appreciated, What am I doing wrong here ?:confused:

---

### Post by aysiu on 2006-10-20
Freezes occur for one or more of the following reasons:
1. Hardware failure.
2. Corrupt installation disk (corrupted during download and/or burn)
3. Not enough RAM (less than 256 MB)

I'm betting it's #2. Did you do a checksum? If you have no idea what that means, you need to read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Kateikyoushi on 2006-10-20
You downloaded the right cd, that should run from the disc, but seems you have a compatibility issue.

You can try these commands to be able to run the disc.

At menu F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by glug101 on 2006-10-20
> **Davec1 said:**
> I have always wanted to try Linux, and Leo Laporte got me interested, so I am in the process of trying to install Ubuntu 6.0.6 but seem to be stuck. 
I D/Loaded the .iso file for i386 Desktop, and burned it to  a CD.
All appears to be ok.
When I boot, it boots from the CD and goes right to the options screen where I choose to Start.
It then goes to the screen with Ubuntu  symbol on top and below, it says.... Load essential Drivers.      OK
and ....Mount Root file system.
After that it freezes, and eventually I have to shut down.

When downloading the Ubuntu files there were so many I got a little confused, I wanted the one that runs from the CD without installing it.
I may have the wrong one here...
 Any help will be much appreciated, What am I doing wrong here ?:confused:
How much ram do you have on the computer?

Edit: Yikes, everybody at once!

---

### Post by Davec1 on 2006-10-20
I have 1gb of ram so that should be enough..I think

---

### Post by Kateikyoushi on 2006-10-20
That's more than enough, try what I post above because assuming from your ram you have a newer system and compatibility might be the cause.
If you know your config post it so we know what we are dealing with.

---

### Post by mythandros on 2006-10-20
I'm having a related problem.  The Ubuntu install hangs right where all you see on the screen is "Ubuntu" and a progress bar.

- I'm using a pioneer dvd/cd rw drive
- I've already gotten WinXP up and running on this system with relatively few problems.
- I cannot boot a known good copy of knoppix from my dvd drive
- I've run bootable cds with diagnostic tools on them from this drive before

I'm wondering if it's not my motherboard (ASUS M4N32-SLI) that's causing the installations to hang.

---

