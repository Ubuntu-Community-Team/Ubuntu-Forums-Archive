---
title: "Install problems w/IT8212 controller"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by the kaz on 2006-06-27
Hello all,
as my search here yielded no answer to that question (though did find out that the ITE controller is somewhat problematic) - is it at all possible to do a fresh install 6.06 when all your optical drive are connected to a IT8212 controller? So far, I've had no luck whatsoever with both the CD and DVD versions of 6.06 using the various install options - either the install simply hangs early on the the process, or the install process doesn't find the optical drive anymore when it fires up. As far as I understand it, there is no kernel modules for the controller on the install medium - but I have no other linux on the system (therefore cannot compile anything yet), and couldn't find any patch or kernel module for the ITE controller and 6.06 anyway. Plus, I have to other interfaces I could connect the optical drive to that might work better. 

So, I guess my question is: should I give up? Is there really no way to get Ubuntu installed onto the system?

Gretings, the kaz.

---

### Post by crispingatiesa on 2006-06-28
The way I solved the problem was by putting the optical and harddrive in the "normal" IDE controller (my MB is an ASUS P5GD1) and my second disk in the ITE8212, later I swapped the second disk with the optical and reinstalled grub.


Until yesterday it was working well, now I have some problems with the optical drive (but that's a BIOS problem) .

---

