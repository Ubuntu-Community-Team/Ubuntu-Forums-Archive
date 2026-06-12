---
title: "cannot install xubuntu"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by omeron on 2007-07-14
I have kubuntu 6.06 installed on my IBM 600x and it's way too slow. so I'm trying to install xubuntu 7.04

I get the error message - Buffer I/0 error on device fd0; logical block 0, which means floppy missing (duh!). 
the boot sequence does not look for a floppy, and I don't know what to do. 

any ideas?

Omer

---

### Post by Taino on 2007-07-14
Try the [Alternate CD](http://cdimage.ubuntu.com/xubuntu/releases/7.04/release/xubuntu-7.04-alternate-i386.iso) sometimes the graphical install one causes odd install hang ups and problems, The alternate cd runs more in terminal mode like the early Ubuntu install cd's did.

Check your BIOS settings and make sure your booting off CD first, maybe even turn off booting from floppy all together even if its not selected as the first bootable item.

Possibly even unplug your floppy drive so its not detected or even messed with by the install process.

These are just some random ideas but one might work... :KS

---

### Post by omeron on 2007-07-14
I hope... 

apparantly the IBM BIOS has a special feature called quick boot which is optimized for plug and pray OSs. when turned on (default) the bios doesn't really configure the hardware. when turned off there is no floppy problem.

---

