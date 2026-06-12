---
title: "Ubuntu Server 14.04 broken by automatic updates?"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by mike_anderson2 on 2014-11-14
Hi Everyone.

I have been using Ubuntu desktop for a few years and a couple weeks ago I successfully put together a samba server for our "network" . I'm all we have for IT ( very small company ) and am a mechanic by trade.

I set up the hardware thusly:

ECS A960M-MV Motherboard
AMD FX8120 processor
Crucial 4 Gb memory
Seagate 160 GB SATA drive x 3 (software RAID 5)

All parts are used but were removed during upgrades of other computers, not due to failures.

During the installation I successfully set up the software RAID 5 on the 3 drives, then selected to install smb server and ssh server and ( here is where I think I erred ) automatic updates.

During the first week of operation it worked wonderfully. I was able to ssh into it and set up the cifs shares for anonymous access for our needs and copied from our old dying server ( celeron w/ 1 IDE drive ) everything we had there. Set up backup from one of the connected machines to a dedicated backup drive and thought life was wonderful.

Then on Monday the shares could not be accessed and I could not ssh to the machine. Connected a monitor and saw:

error : attempt to read or write outside of disk 'hd0'
Entering rescue mode ...
grub rescue> _

So I have looked into the probable fixes for this but before I dive into that... was I wrong to enable automatic updates or is it more likely something else?
I'll be getting the box out of it's cubbyhole to work on now.

Thanks for your time and thoughts.

mike

---

