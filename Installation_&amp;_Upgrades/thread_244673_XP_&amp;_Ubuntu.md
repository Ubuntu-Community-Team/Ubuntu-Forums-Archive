---
title: "XP &amp; Ubuntu"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by zoob on 2006-08-26
Machine Specs:

Asus A8N-E Motherboard
AMD Athlon 64 X2 4200+
2GB RAM
2 SATA Seagate ST3250824AS 250GB Drives
1 SATA Seagate ST380817AS 80GB Drive
Lite-On DVD-ROM
BENQ DVD-RW

I have been using this system with a single 250GB and 80GB dual booting with GRUB with XP on the 250GB and Ubuntu on the 80GB.  All was well, and I loved Ubuntu and had it tweaked.  Hard drives dropped in price, so I bought another 250GB and used the RAID controller to mirror the 250GB drives for redundancy.  When I did this I lost my GRUB as expected.

I used several different methods in this forum to try to reinstall GRUB to no avail.  So I reinstalled Dapper to the 80GB again.  Upon rebooting I still did not get the GRUB menu.  Anyone have suggestions?  Is the XP NVIDIA mirror not compatible with GRUB or am I missing something on the installation?

](*,) ](*,) 

Thanks in advance for your help.

Kevin

---

### Post by zoob on 2006-08-29
Got it!  And so simple I feel bad for posting it, but I hope this helps someone else.  Go into boot and pick the Ubuntu drive to boot first and Viola!  Grub appears!

Thanks all,

Kevin

---

