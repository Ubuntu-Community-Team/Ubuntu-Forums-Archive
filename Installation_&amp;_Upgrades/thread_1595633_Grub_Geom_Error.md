---
title: "Grub Geom Error"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by nolegjoe on 2010-10-13
Hi,

I tried to install Ubuntu 10.10 today alongside Win7 on my desktop but after the installation I was unable to boot into either and I keep getting geom error on boot. I'm fairly certain that I've done something stupid with my MBR but need some advice.

Basically, my computer has 3 internal hard drives. I have a 500GB, a 10GB and also a 200GB drive. Originally, I had a working copy of Win7 running on the 500GB and I tried to install Ubuntu onto the 200GB. For some completely unknown reason, my bootloader was always located on the 10GB drive. Originally, this has never caused too much of an issue until now. To make things worse, I believe I have another bootloader on one of the other drives which seems to point to an old Vista installation that I have since removed. This was never a problem until now. I believe, my setup worked like this...

The 10GB drive was listed in BIOS as the primary boot drive and would point it too the 500GB drive
The 500GB drive had the Win7 OS installed on it
The 200GB drive was always bypassed by the BIOSs boot sequence.

Ultimately, I'd like my system to work like this...

the 10GB drive has GRUB on it that listed Win7 and Ubuntu 10.10 and points to both the 500GB and 200GB drives.
The 500GB drive has Win7 on it
the 200GB drive has Ubuntu on it.

is there any kind of MBR fixing program that can sort out this mess for me that I can put on a live boot disc?

---

