---
title: "&quot;starting hotplug subsystem&quot; freeze"
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by dmallery on 2005-03-19
hi

i have the newest hoary preview.  the machine has a supermicro 370 de6 mobo with a pair of p3 1000s.
during the reboot phase of the install, the machine gets to "starting hotplug subsystem", does a few disk accesses and then just sits there.

i think i have tried every permutation of noapic pci=noacpi acpi=off noacpi plus the mobo cmos option of acpi-aware o/s.

the results seem the same as with the warty install disk.  the warty live cd also freezes.

actually "freeze" is not accurate.  there are several disk accesses after the "starting.." message and i can turn the machine off with the power button.  also, i have waited many minutes on each test to be sure i was not jumping the gun.

the same machine boots knoppix 3.6 with a 2.6.7 kernel.  it has trouble starting x11. but startx works. it can start the same knoppix perfectly if you use the default 2.4 kernel.

i wonder if i am barking up the wrong tree here.

any help/clue/pointer will be gratefully received!

thanks

dave mallery

---

