---
title: "No list of operating systems"
date: 2012-01-06
forum: Installation &amp; Upgrades
---

### Post by thvan on 2012-01-06
So, I finally came around to installing ubuntu, aiming for dual boot system, along side W7.

Ubuntu [probably] installed perfectly, however, I'm not able to actually boot ubuntu.

I have partially given up, understanding bl, mbr and so on, as this is really the first time I've had dual boot with a none Windows OS. I was under the impression, that ubuntu would fix the mbr, so that I could be able to choose either OS.

Technical stuff..
I have two hdd installed. hd0 has 3 partitions, with W7 installed on partition 0 - Partitions 1 and 2 are NTFS partitions, only used in that W7 installation, and only contains files etc.

Second hdd had (before ubuntu installation) two partitions, partition 0 was chosen by ubuntu installation. Partition 1, again a NTFS partition.
Ubuntu install created a total of 3 partitions, and the hdd currently looks like this (taken from easyBCD)
hd1,0: swap [10gb]
hd1,1: NTFS [148gb]
hd1,2: Linux [137gb]
hd1,3: swap [3gb]

Now, what I would like, is links, basic info, tips and tricks for creating a mbr, installing grub - anything really, that would make my pc actually booting ubuntu, and my able to choose which os I want to boot.. :-)

Even though I have been using both ubuntu and windows separately, I'm somewhat of a novice in this department.

---

### Post by darkod on 2012-01-06
Have you tried to set in BIOS to boot from the second hdd as first option? If ubuntu was installed correctly most probably grub2 bootloader is on the mbr of that hdd. If the computer is still booting from the first disk it will keep loading windows directly since it can't see linux.

Another thing is why would you have two swap partitions since you only need one (if it's true that they are both swap partitions), but that's not a big problem. In fact it's not a problem at all except that the space can be used better.

---

### Post by Quackers on 2012-01-06
Nowadays HDD's start at 0 but partitions start at 1 (unless you use grub legacy rather than grub2).
In other words the first partition on the second disc would be hd1,1 - not hd1,0

---

### Post by Mark Phelps on 2012-01-06
If you do boot from the second drive, and it boots right into Ubuntu, then once there, open a terminal and enter "sudo update-grub".  This will update the GRUB menu and you should see it find Widows on the drive as it works.

Once you then reboot, you should be presented with a menu of OS selections, including both Ubuntu and Windows.

---

### Post by thvan on 2012-01-07
> **darkod said:**
> Have you tried to set in BIOS to boot from the second hdd as first option? If ubuntu was installed correctly most probably grub2 bootloader is on the mbr of that hdd. If the computer is still booting from the first disk it will keep loading windows directly since it can't see linux.

Another thing is why would you have two swap partitions since you only need one (if it's true that they are both swap partitions), but that's not a big problem. In fact it's not a problem at all except that the space can be used better.

Nope didn't try that - Worked a charm though... So simple :\
Thanks a bunch! :-)

Sorry Quackers, I'll keep that in mind..

Mark Phelps: Won't be necessary, worked as soon as I switched to boot from the hdd with ubuntu on it, thanks!

---

