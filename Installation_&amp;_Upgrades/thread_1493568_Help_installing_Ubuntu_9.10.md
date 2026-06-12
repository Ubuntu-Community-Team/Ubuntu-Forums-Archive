---
title: "Help installing Ubuntu 9.10"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Hitman7112 on 2010-05-26
Okay I am a experienced Windows(7) user, and I want to switch to Ubuntu for good but I feel like I am on an alien planet, because everything is new and unknown. 

Specs (if needed):
Dell Inspiron 1545
3 gigs ram
145 gig HDD
Intel Pentium Dual-Core
Windows 7 32-bit
2.6 GHz

I want to partition Windows 7 so I can dual boot it with Ubuntu but I get this error. Do I click yes or no???
[IMG]http://lh6.ggpht.com/_zia4uyESsZc/S_ykXIQJZKI/AAAAAAAAAtI/nv23N9jJaa8/s800/Problem2.png[/IMG]

I clicked no just to see what would happen, so I got this.

[IMG]http://lh5.ggpht.com/_zia4uyESsZc/S_ytiwLJPiI/AAAAAAAAAtY/PVooadydNSs/s800/Problem.png[/IMG]

I clicked the advanced option on picture number 2 because I obviously do not want to remove windows 7, i want to simply dual boot. I have seen other people installing it where it gives them colors for sda1 and sda2 and so on but I only get green. I also do not get the option to install Ubuntu along side Windows 7 like in other cases.

Then finally I get this after clicking forward.
[IMG]http://lh5.ggpht.com/_zia4uyESsZc/S_ykXl-yEuI/AAAAAAAAAtQ/ibtrZ_JbfQE/s800/Problem3.png[/IMG]

Any help would be greatly appreciated, thanks in advanced. ~Daniel (Dam I feel stupid, I guess that is what years of using Windows does to you =P)

---

### Post by kansasnoob on 2010-05-26
You should only resize Win Vista and Win 7 with their own partitioning tools!

[http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista)

---

### Post by darkod on 2010-05-26
Yes, decide how much you want to shrink the win7 system partition. You need to give ubuntu at least 25GB-30GB, even more if planning to keep large videos/music/photos inside.

Use win7 Disk Management to shrink the partition. Leave the created new space as unallocated. Reboot win7 few times to make sure it's happy, it might want to do some disk checks after the shrink.

When that is done, boot with the ubuntu cd and start the installer, in step 4 just select the option Use Largest Available Free space. That will install it inside the unallocated space you left.

That's enough for a start. :)

---

