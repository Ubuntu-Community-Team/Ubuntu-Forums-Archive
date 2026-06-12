---
title: "nForce 4 SATA RAID0 detected as single drives"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by Mozgus on 2007-04-07
I've done some searching, and I see a tool known as mdadm being mentioned regarding SATA RAID problems. I cant seem to find much instruction on using it to fix my problem though.

Board: Asus A8N5X Socket 939
Drives: 2x Western Digital 80GB 7200RPM S-ATA HDDs (3rd one on it's way)

Now as far as I'm aware, my board creates a true hardware RAID, rather than a software RAID. So I was surprised to see an OS somehow detect these as two separate drives.

Does anyone know of a solution I can make use of during the Live CD installation process? I am hoping to install Ubuntu (in a stable fashion) on my RAID-0. I'd especially love it if I could shrink down the existing RAID-0 and make a new partition from it, like the method which works perfectly on my IDE drive. I currently have XP on the RAID-0, and don't want to reformat unless I have to.

Thanks.

---

### Post by GrammatonCleric on 2007-04-07
You might want to check out the following post.  It helped me with getting my nvidia raid working. 

[http://ubuntuforums.org/showthread.php?t=299518&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=299518&highlight=mdadm)

-GC

---

### Post by Mozgus on 2007-04-07
> **GrammatonCleric said:**
> You might want to check out the following post.  It helped me with getting my nvidia raid working. 

[http://ubuntuforums.org/showthread.php?t=299518&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=299518&highlight=mdadm)

-GC

Hmm I dont really follow that. I found this, but it's even more complicated:

[https://help.ubuntu.com/community/RaidConfigurationHowto](https://help.ubuntu.com/community/RaidConfigurationHowto)

No chance for me. I fail at step 1.

OK this one seems better suited for me:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Mozgus on 2007-04-09
Should I instead download the Alternate Install CD? It seems to indicate RAID support in the description.

---

