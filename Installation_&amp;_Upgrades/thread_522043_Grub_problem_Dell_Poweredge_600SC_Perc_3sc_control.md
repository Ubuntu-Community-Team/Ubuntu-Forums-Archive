---
title: "Grub problem Dell Poweredge 600SC Perc 3/sc controller"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2007-08-10
Trying to install 7.04 server onto a Poweredge 600SC with Perc 3/SC controller and a pair of 300Gb disks configured as RAID-1 on the controller. The installation goes without a hitch, I select the default of installing Grub on the MBR of the first hard disk, but on on boot after the install completes, absolutely nothing happens at the end of POST - no Grub messages of any sort. 

If I boot again off the install CD and select the option to boot from the first hard disk, then I get the normal Grub menu and can boot into Ubuntu without any problem.

I tried the install twice with exactly the same result. The Perc controller and server BIOS are both at current Dell firmware levels.

---

