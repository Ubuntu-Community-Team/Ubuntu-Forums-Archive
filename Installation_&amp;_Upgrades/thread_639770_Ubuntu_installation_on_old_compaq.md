---
title: "Ubuntu installation on old compaq"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by Roflcopter939 on 2007-12-13
Disclaimer: Still an ubuntunub
Now, I've installed and used Ubuntu on a few other computers in the past, and never have I had as many problems as this.  When I try and load from the livecd, ANY of the options gives me the same error

ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 

That being said, I have no idea what any of those numbers means.
Now, I have XP installed on the computer already, and it runs fine.  It is an older PC, but what I think is causing the problem is the Intel Boot Manager that's installed, and runs every time the computer is started.  I've been looking on the forums to install Grub, the easiet way I'd thought of to get rid of the Intel Boot Manager.  The problem is that all the options I've seen assume you can get INTO the livecd and run the terminal.  Any thoughts?

OS Name: Microsoft XP Professional
Version 5.1.2600 Service Pack 2 Build 2600
System Manufacturer Compaq
System Type X86-Based PC
Processor x86 Family 6 Model 6 Stepping 5 GenuineIntel ~498 Mhz
Bios Version/Date Compaq 686C2, 10/3/2000
SMBIOS Version 2.3
Boot Device \Device\HarddiskVolume1
Total Physical Memory 512.00 MB

EDIT: I've downloaded supergrub, and attempted to use it to no avail.  It can't be the hard drive if windows XP works right?

---

### Post by Craigus on 2007-12-13
So, you are able to boot from the CD and see the initial menu screen ? If so, the other boot manager is not running and cannot be the cause of the problem.

Have you tried the alternate CD ?

---

### Post by Roflcopter939 on 2007-12-13
I'm not sure what you mean by alternate CD.
Initially I was setting this up as a server, so I downloaded the server version of Ubuntu, but I must have made the cd wrong because it won't boot from it.  I haven't tried to make another server version so I just used my workstation 7.10 disk.  Is there a different 7.10 cd?

---

### Post by Craigus on 2007-12-14
> but I must have made the cd wrong because it won't boot from it.

But it is booting as far as the initial menu, is it not ?

There could well be a problem with a bad CD burn or corrupt .iso download - have you checked the MD5sum of the .iso ?

There could also be a hardware compatibility issue, which is why I suggested the alternate CD. There is a version that is more compatible with a wider range of hardware.

If you haven't checked the integrity of the .iso file and also tried burning another CD at a slower speed + / - different media, I'd suggest those approaches first.

---

### Post by Roflcopter939 on 2007-12-18
So I've recently installed Gutsy on my friends laptop with the workstation cd I made, with no issues.  Like I said, my workstation cd booted fine, what I couldn't get working was the server edition (which is why I have this doorstop on my desk in the first place).  Hardware issues is definitly looking to be the problem I was just wondering if there was a known fix for that error on older machines.  I'm downloading the alternate cd now, so we'll see how that goes. 
 What scares me is Googling the error message, the only resolution I've found is that the hard drives got thrown away and replaced, and this is a fairly new hard drive (not technology-wise, but referring to its hours in operation).  I'll let everyone know how the alternate cd works and thanks for the suggestions! :p

---

### Post by Craigus on 2007-12-19
If the box is going to be purely a file server, you could have a look at FreeNAS:

[http://www.freenas.org/]("http://www.freenas.org/")

---

