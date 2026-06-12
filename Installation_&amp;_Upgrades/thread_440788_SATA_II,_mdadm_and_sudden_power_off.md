---
title: "SATA II, mdadm and sudden power off"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2007-05-11
I can't get my new desktop working with RAID 1. I can create a small RAID 1 partition, but on a large one I get a sudden power off.

Hardware:
Abit NF-M2S motherboard
	nVidia 405 chipset, including 2 SATA II connections
	Realtek 8169SC gigabit
	nVidia GeForce 6100
AMD2-64 4600
(2) DVD+-RW dual layer on ATA, master and slave
(2) Western Digital 320 GB SATA II 
(2) Corsair 1 GB DIMMs 533
Antec 500 Watt PS with two 18 amp 12 volt rails

That's it. No add-in cards. I use the ethernet and video on the motherboard.

The problem is is the sudden power off when mdadm tries to set up a large RAID 1 array. It goes for anywhere from a few seconds to maybe 30 minutes max, then suddenly the whole computer shuts down. No warning, no log files. It's like someone pulled the power plug out of the back of the case.

I have:
Replaced the power supply (the original was RaidMax 380 watt)
Swapped the motherboard
Replaced the SATA II cables
Run memtest86 on the RAM
Run Western Digital Lifesaver Diag utility on the hard disks
	This utility does not know about RAID, so it tests one disk at
	a time. It ran for 75 minutes on each drive, no errors

There are three RAID 1 arrays:
/dev/md0	2 GB	swap
/dev/md1	40 GB	Feisty amd64
/dev/md2	20 GB	Empty, formerly Etch amd64

The md1 and md2 arrays check out fine with e2fsck. However, half the time Feisty won't finish booting before I get a power off.

Plus I am trying to create another RAID 1 array: /dev/md3 238 GB for storage of backups

It is the creation of /dev/md3 that is causing the problems. Just now I decided to reinstall Etch on /dev/md2 to see if its installation utility could create the /dev/md3 array as part of the setup process. The partitioner got to the formatting of /dev/md3 and suddenly I had a power off again. In other words, there is something about creating that large RAID 1 array with mdadm that is causing the problem,mI have checked bug reports on mdadm and the only thing I can find is corrupted data; nothing like this problem.

I have spent hours googling and have come up with nothing. 

I have spent hours fiddling in the BIOS hoping to stumble on something that solves the problem. "Failsafe" and "Optimized" settings do not work, nor did the original factory settings. The "SATA spread" has two options, Disabled and Triangular Down. Neither makes any difference.

It is not heat related because the heat settings in the BIOS are disabled, plus it happens even with the computer is stone cold and has just been turned on. Several times I have viewed the temp display in the BIOS and the system and CPU temps never get above 32 C.

*Something* is sending a kill signal to the power supply, i.e., the soft power off is being triggered. I am assuming it is the same signal that the OS sends at the end after the user has clicked on the Shutdown icon. The mystery is what could be doing it. I wish I knew how the soft power off works.

Any ideas and suggestions welcome, regardless of what wild hair spawned them. This is a killer box and I want my Feisty working on it!

---

### Post by John Jason Jordan on 2007-05-15
It took forever, but I finally fixed it. The problem was that I thought the NF-M2S motherboard had the latest BIOS (version 1.1) because that is all that was listed on abit-usa.com. But on abit.tw there are two newer ones. I just finished flashing the BIOS to 1.5 and the problem seems to have disappeared. <Crossing fingers>

---

