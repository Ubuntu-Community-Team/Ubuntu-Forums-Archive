---
title: "Partitioning for Dual Boot Windows"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by gothrabbit on 2008-02-21
I have a formerly-Windows 2000 machine with a brand new 160 GB HD.  I want to have a dual-boot Ubuntui/Win2K machine when I am all done.  However, due to the old version of BIOS, the machine isn't playing nice with the 160GB HD (the partition software that came with the drive is kind of crappy).  So I am starting with the Ubuntu install and then am going to add Windows later.  

Should I partition the drive in the Ubuntu install to allow for a free partition for Windows? (If so, tips on how to do?)  Or should I go ahead with the Ubuntu install on the whole 160 GB drive and then repartition it later for my Windows partition (found the link on the forums and bookmarked it)?

I'd like to do this the "right" and "least painful" way so that I don't have to cause myself more headache later (this machine has caused me enough headache for a lifetime at this point, can't wait to have Ubuntu on it!)

Thanks!
Rebecca

---

### Post by Pumalite on 2008-02-21
How many GB's does your BIOS "see"

---

### Post by gothrabbit on 2008-02-22
After going blindly ahead and then reading a lot to figure out why things weren't working, I see why you asked. ;)

BIOS sees about 32 GB, so it's the 2 generations old BIOS.

I tried partitioning it in 3 via the Ubuntu install (1 small partition for a separate boot area, 1 partition for Ubuntu, and 1 for Windows...well actually 4, including the swap partition).  So far I am still struggling with getting the boot partition to work correctly, following the [GRUB instructions on how to make a boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").

Is this the best way to go about this?  I don't mind starting over and re-partitioning it, if necessary.

---

