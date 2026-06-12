---
title: "Setting up partions manually due to large drive"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by methodical on 2007-12-30
I had recently installed Ubuntu server edition on an older PC and the hard drive I had it installed on (80gb) crapped out :confused:

I have a 500GB drive that my bios does detect, but now that I have installed Ubuntu server on it I am getting Grub error 18. Now I know this means that the drive is to big for the bios to boot from, but I have read that if you make a smaller boot partition it will boot and LInux will detect the drive.

How big should the boot partition be? If I go to setup the partions manually do I have to set up each mount point separately or can I just setup the boot and swap and use the rest of the disk for everything else?

I hope that made sense. Thanks...

---

### Post by logos34 on 2007-12-30
Have you [read this]("http://users.bigpond.net.au/hermanzone/p15.htm#18") first and checked Bios hard disk detection mode? Or flashed the Bios with update?

100 mb should be more than enough for a /boot partition.  Create the /boot and /swap first, then give the rest to / .
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

