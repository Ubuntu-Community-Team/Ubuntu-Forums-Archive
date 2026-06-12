---
title: "Grub Error 17 After System Upgrade"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by kulturloseramerikaner on 2010-02-25
I moved last summer and the mobo on my old system didn't survive the trip. I finally got around to getting myself a new processor and mobo a week ago, but I haven't been able to fully restore my system.

I was happily triple-booting 8.04, PC-BSD, and Win XP before, and each on its own hard disk. I decided to add Win 7 as I got it on the cheap to have a game playing platform. After the build, the install of Win 7 went off without any issues. I've added back the drives containing the other 3 os's though, and am now having trouble.

Even after removing the cable to the Win 7 drive and putting the original 3 drives in the correct (I'm pretty sure) SATA ports, I get GRUB error 17. This but isn't even the weird part; GRUB itself loads to the selection screen but trying to boot either 'nix system is no good, it says it can't read either the 'Buntu or BSD drives (invalid file system type). If I tell it boot XP though, it gives me the XP splash screen no problem, then BSOD's because it doesn't yet to know what to do with the new mobo/processor combo (I'd like to resolve the boot issue before I run an XP repair install if I can.)

I'd like to get myself able to boot all 4 os's; currently I'm able to use Win 7 as long as I pull the SATA cables to the other 3. Supergrub has not helped, nor has downloading 9.10 to liveCD because of the GRUB2 switch there (can't find my 8.04 disk.)

I'd greatly appreciate any help or pointers to get me going in the right direction on this. I miss my Linux too much.

---

