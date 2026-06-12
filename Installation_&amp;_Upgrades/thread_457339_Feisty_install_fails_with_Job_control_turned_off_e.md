---
title: "Feisty install fails with Job control turned off error"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Freymish on 2007-05-28
I downloaded an ISO image of 7.04 and am trying to install to an HP Omnibook XE3.  The install begins but fails after trying to access the floppy drive.  I am assuming this is an unrecognized hardware issue from the other posts I've seen.  The error is:

"/bin/sh:  can't access tty;  job control turned off"

I am new to Ubuntu and have only dabbled with Linux in the past.  The HD is blank and I am assuming that the install process will give me the opportunity to create the partitions later on.  

An update:

I stuck a random floppy in and tried again.  This time I got further before the thing locked while loading the GUI

Please help.

Freymish

---

### Post by shrimants on 2007-07-04
the problem is that you have an HP laptop. HP completely locks down the BIOS, and that is what is causing the error. i myself have this problem and it took a while before i realized why. im currently trying to find some sort of bios unlocking utility or even a fresh bios because everything with HP is completely jammed up. i cant even install Sabayon linux because HP is stopping the installer from accessing yhe CD drive. bad things.

---

