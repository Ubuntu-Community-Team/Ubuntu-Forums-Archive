---
title: "Need help to repair kernel - file not found"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by tort43 on 2010-03-22
When I attempt to boot into Ubuntu 9.10, I get the error:  "Error 15: File not found"

I know the reason for this - I deleted it - Doh.

A latest upgrade told me I didn't have enough room in the boot partition to install the latest files, so I thought it would be a marvellous idea to remove the old stuff, to give it some room.  I obviously deleted something that I needed by mistake.  I was using synaptic to do the remove & thought I would be safe.  A good learning experience.

In grub menu I have options:  Kernel:  2.6.31-15 - generic   and also its recovery option, both of which get the same error.  
(It's a dual boot with XP as the original os).
 
Ideally I'd just like to get the latest working kernel and put it somewhere appropriate, rather than do a full install.  Is this possible and if so how?  I have a separate boot partition (in dev/sda5), swap (sda7) and Linux (sda6).

I have a 9.04 livecd I can boot.

TIA!

________ SOLVED _______________________________________________

mounted the boot partition (to /media/karmic)
and saw that it contained kernel 2.6.31-20 files
so changed grub menu.lst to point to those and rebooted
and it booted ok.

Then I wanted to check the kernel is ok, because I think this version was the one that did not install correctly because of lack of disk space, so
sudo apt-get install linux-image

---

### Post by pdro7 on 2010-03-22
hi, i'm having some problem like yours , after and upgrade my sistem collapse, and the kernel file dissapear, have u solutionated the problem??
thanks

---

