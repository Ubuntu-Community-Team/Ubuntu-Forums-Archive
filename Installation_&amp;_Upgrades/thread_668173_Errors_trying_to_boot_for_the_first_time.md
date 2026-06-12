---
title: "Errors trying to boot for the first time"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by rockydeboxer on 2008-01-15
Hi, I installed a total of 3 HP Netservers LH4r, with integrated NetRaid controllers (Megaraid) and the installation of Ubuntu Gutsy worked fine in all cases. The first boot doesn't.

The one machine has trouble mounting the root partition or gives a segmenation fault. The second machines has trouble mounting the root partition or gives a bus error and I/O buffer problems. The third machine did fine at first but starting giving me trouble with mounting the root partition yesterday.

I looked at all the forums, and I guess I have seen all the threads regarding boot errors by now, but none of the solutions seem to work.

I tried to change boot parameters with irqpoll, ide=nodma acpi=off and more, in every combination possible, but no result. At least not all the time. Sometimes it seems to work, sometimes it doesn't.

I tried to change the boot parameter for the root=/UUID to root=/dev/sda1, what seemed to work at first, but after encountering more problems and reinstalling the machine (again) it didn't anymore.

I set my NetRaid configuration from Mass Storage tot I2O and back. 
I disables my integrated COM, Parallel and integrated management ports to save some IRQ's which also gave me trouble.

But, till this day, I still get the mentioned problems almost at random.

I have even tried to install Fedora 8 which installed fine on one machine, but the installation interupted on the other two, because of a file missing or corrupt. This also couldn't be the issue, because the same DVD installed fine on the first machine.

I hope anyone can help me pinpoint and solve this problem, because I really need a stable server that I can use to host my mail and sites.

Thanx

---

