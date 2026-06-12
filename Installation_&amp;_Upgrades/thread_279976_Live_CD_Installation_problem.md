---
title: "Live CD Installation problem"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by oldgeek on 2006-10-18
I attempted to run the 6.06 Live CD on a friends pc using the same CD that I have successfully used on this, my own pc to run and install.

Here is the problem:

Boots OK and then at the "Mounting filesystem...." after several minutes instead of "OK" it goes into text mode and displays:
> [17179571.848000]..MP-BIOS bug 8254 timer not connected to IO-APIC
[171.........]..PCI Cannot allocate resume region 3 of device 0000:00:00.0
[171.........]..hdc: ide_intr: huh? expected NULL handler on Exit
.
.
.and more of similiar info

I assume this info will continue on forever so bailed after several minutes of this.

I added pci=noacpi to the boot sequence but still fails.

Hardware is a New Compaq System:
Presario SR1930nx - P4/SATA/512M Ram. Graphics, etc. onborad.

Since this is a new system with pretty standard chip set I am surprised.

Any Help?


Rong

---

### Post by gn2 on 2006-10-18
Had a quick look at that PC's specs and it seems to have a problematic graphics chip..... ATI Radeon Xpress 200

That might be unrelated though...

Have you tried another Distro? I recommend PCLinuxOS

Are you related to theeldergeek ? ( [www.theeldergeek.com](www.theeldergeek.com) )

---

### Post by oldgeek on 2006-10-18
Thanks for reply.

The ATI chip issue is good info. I'll toss in another graphics card tomorrow and rule that in or out.

Nope, I'm not related to the oldeldergeek but obviously it appears we do have much in common!

---

### Post by Simulationcity on 2006-10-18
You're lucky you got that far. My CD doesn't even do anything.

---

### Post by oldgeek on 2006-10-19
This kind of thing is the downside of Linux.  I've used a number of distros on quite a few different pc's and getting consistently good results still ranks low.  Worth the effort though!!

---

