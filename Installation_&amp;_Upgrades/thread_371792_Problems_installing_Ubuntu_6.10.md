---
title: "Problems installing Ubuntu 6.10"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by Mickey1 on 2007-02-27
The PC

Hp pavillion a414x 
Lite-on combo cd writer/dvd-rom
Sony DVD RW
1024 MB RAM
280GB over 2 drives
1. Maxtor 200GB
2. Seagate 80GB

I currently have a dual boot setup but not a good one 
Both are windows partittion as i had a slight hickup with old OS wich had enough content wich i could not afford to lose 

Other Specs:
ATI 9250 
Onboard Audio ac'97
Onboard video present too but dunno precise specs

Previous Distros this pc has seen 
1. Ubuntu 5.10 Breezy Badger

The disc i downloaded from the website was checked for the md5checksum with winmd5sum
That came out to be a match

Burning the disc using Infra Recorder (which is recommended on your website) failed as it decided to reboot halfway though

Then burned with Nero
Verified written data all was ok

Boot Methods:
I come to the prompt and select F6
I enter acpi=off behind the scribble that's allready there( searched for this "fix" for ages)

So no more interrupt errors

Then when it does load i get the following error message
Kernel Sync failed (i believe)
EIP:c01143c1
*PDE 00004067
Oops: 0003 [#32]
SMP 
and then another scribble


When i installed 5.10 Breezy badger i had some serious issues with my ATI card and am wondering if this could be the same

Many thanks in advance

---

### Post by Mickey1 on 2007-02-27
After messing around in the bios disabling plug and play and removing my ATI card and using the onboard i appeared to have made it with the Live CD part

Now the installer hangs every time i wish to access the partitioner

Does anyone know how to take care of that?

---

