---
title: "Vista 64,XP and Ubuntu"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by michael674 on 2010-05-29
OK, be patient with me, I am a noob. With that said I have (4) 320 GB SATAdrives set up as raid 10 or raid 01 as they say it, These drives are on my 0,1,2,3 ports of my mobo. It is on a DX38BT Mobo with all 4 running Vista 64. I have a 500 GB SATA drive that I would like to partition and set up with XP and Ubuntu. for some reason (noob) I am having alot of problems. I think that it might be Grub and it is in conflict with the raid controller. I appreciate any help.
Mike

---

### Post by darkod on 2010-05-30
You didn't specify what kind of problems you are having. Also, you will not be running any OS on the RAID, right?

In theory, the process would be:
1. Make the 500GB disk first option in BIOS in hdd boot order. Boot with the XP install cd, make a partition on the disk with the size you want for XP (do NOT let it take the whole disk) and install XP. Check that it's working fine.

2. Then boot with the ubuntu cd, and either use the guided method Use Largest Available Free space to install on the rest of the 500GB disk, or use manual partitioning for more specific setup.

That should be it.

However, if you plan to specify mount points for ubuntu during install which are on the RAID array, I'm not sure it would work. In fact, I'm confused what do you want to use the raid for and at which moment you want to implement it.

Because for example, for raid support you need to use the Alternate Install CD for ubuntu, not the standard desktop image.

---

