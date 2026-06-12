---
title: "PXE  error on Dual Boot"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Zimmer on 2009-12-03
Having set up a Vista laptop with a dual boot installation ( GRUB loaded to Ubuntu partition, not MBR to allow EasyBCD in Vista to control initial boot)
I was greeted on the  restart with a boot error.

PXE-53 No boot filename received
PXE M0F

The laptop had tried to boot from LAN, so searched the web for answers, which were varied and mostly   'incomplete'  involving changing boot order etc..

The solution to this particular problem was very simple.
 On install and partitioning I had asked the partitioner to set the boot flag on the Ubuntu partition.

This left the Vista partition with no boot flag...

This was rectified by booting from the live cd and running the partitioner and setting the boot flag back onto the Vista partition 
 On restart I was able to boot Vista and update EasyBCD with the new Linux install..  

I hope this is of help.

---

