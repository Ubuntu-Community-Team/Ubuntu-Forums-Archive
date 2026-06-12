---
title: "RAID-1 in existing system"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by g0ng on 2008-11-01
Hello,

I bought 2x500GB SATA for a RAID-1. 
I made two partition in each one. A 495GB and a 5GB for swap.

I installed the two SATA disks in my "home server" and created 1 md device with the 495GB partition and created two lvm, one for / (50GB) and one (th e rest) for /opt.

Unfortunattely my old home server's BIOS  didn't recognized the SATAs and it couldn't boot.

So I want to install the in my desktop PC. This computer currently has a /dev/sda where /dev/sda1 has an ubuntu / partition and sda2 has  windows partition.

Let's say I install those 2 SATA disks in my computer. What I want is to transfer my current setup to the RAID. 

First of all can I have a dual boot, where the linux will be on the RAID devices, and windows will be in /dev/sda2 where they are now?

I can mount the 2 disks, make the RAID and copy / to my lvm that will hold the /. How can I point grub to load linux from the RAID and windoes from sda2?

thanks

---

