---
title: "installion via RAID problem"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by derrekito on 2007-04-25
I was trying to install the 64-bit edition of Ubuntu on my Desktop, but ran into a partition problem.  My two 74-gig hard drives that are in raid (controlled by the motherboard) show up as two separate devices.  I'm on windows (same machine) running the OS over the raid.  I'm trying to wipe out the partition and dual boot the system.  So why would the installation see the two devices and not just the raid?

---

### Post by jrouss on 2007-04-25
I am in the same boat and very confused as to how I tell grub that for X64 to boot

---

### Post by pepsi_max2k on 2007-04-25
try searching the forums. i've lost count of the number of times i've seen this raid problem pop up in the last few days.

---

### Post by derrekito on 2007-04-25
> **pepsi_max2k said:**
> try searching the forums. i've lost count of the number of times i've seen this raid problem pop up in the last few days.

yeah lots threads, and no answers that work.

---

### Post by punkybouy on 2007-04-25
Windows has a driver which allows it to use the RAID chip on your motherboard.  Linux does not so it sees two drives.  I doubt the RAID chip manufacturer has a driver for linux but I would start there.  In Windows sometimes there is native RAID card driver and sometimes for some raid cards (at least in XP and 2000) you had to hit the F6 key at installation startup to load the driver first thing. 
There are ways to mirror drives in Linux but they can be clunky to implement

---

### Post by derrekito on 2007-04-25
> **punkybouy said:**
> Windows has a driver which allows it to use the RAID chip on your motherboard.  Linux does not so it sees two drives.  I doubt the RAID chip manufacturer has a driver for linux but I would start there.  In Windows sometimes there is native RAID card driver and sometimes for some raid cards (at least in XP and 2000) you had to hit the F6 key at installation startup to load the driver first thing. 
There are ways to mirror drives in Linux but they can be clunky to implement

I'm an idiot!  I forgot i had to slip stream those damned drivers for windows! Ahh Thanks your a life savor! Asus, the manufacturer for my board, does not have a Linux driver for the RAID chip.  How depressing.

---

### Post by punkybouy on 2007-04-27
You could still implement software RAID.  Do a web search on Linux Raid and you will get tons of results although as I said implementing it can be difficult.  Sun has a pretty interesting file system called zeta file system (zfs) not Raid but pretty cool and may find its way into Linux.  There are ways to replicate your data but mirroring the system drives isn't easy.

---

### Post by derrekito on 2007-04-28
I have two 10,000 RPM Raptor drives and was just wanting to utilize Raid for the possible performance boost.  I might just choose to take the hit, but thanks for your replies!

---

