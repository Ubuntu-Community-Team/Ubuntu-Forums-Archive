---
title: "ubuntu installer crashes"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by mahasmb on 2007-09-19
I've been trying to re-install Ubuntu (Dapper Drake) on my laptop for ages now. But my installer always crashes.

For example, I always get this error when I try to format my partition to an ext3 partition:

> 
**Error while creating /dev/hda3**

Be aware that the failure to apply this operation could affect other operations on the list.

What can I do? This is really frustrating.

---

### Post by wingrider101 on 2007-09-20
Try something simple... use a dos or windows bootable disk with fdisk on it, and go onto the hard drive and delete all partitions (yes all of them), then restart the installer by rebooting to CD.  I've found this frequently works if a previous partition is giving you grief.  Other than that, I can't think of anything else to try.

BAM

---

### Post by kellemes on 2007-09-20
Well, you can use DOS..
I personally would choose something like [SystemRescue]("http://www.sysresccd.org/Main_Page") or [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") to setup your system as you want it, create **and** format your partitions so during the installation of Ubuntu you only need to set your mountpoints..
Maybe this will work?

---

### Post by dabl on 2007-09-20
> **wingrider101 said:**
>  windows bootable disk with fdisk on it



Yep, I think FDISK is the way to get that hard drive back to "clean".  There's probably some residual "checksum" or something in the MBR, that needs to go bye-bye.  :)

---

### Post by Herman on 2007-09-20
Use a Qtip (cotton bud), dipped in denatured alchohol (methylated spirits) and wipe your CD/DVD drive lens clean with it.
It could be one speck of dust or a thin oily film on your CD/DVD (optical) drive lens is causing disc read problems. Even if you can play music CDs and read data CDs okay, you could still have a speck of dirty optical drive lens, software CDs are more sensitive.

Don't let cigarette smokers come anywhere near your computers. So-called CD/DVD cleaning discs don't always do the job. With most laptops, the lens is easy to access because it slides our with the CD drawer. The problem with that though is it's also more exposed. Someone could cough or sneeze nearby and that could be enough to dirty the lens.
Most desktop CD/DVD drives keep the optical lens protected inside the drive itself. Those still get dirty eventually and need to be taken apart just to clean the lens and that can be a daunting task.  For some people it would be better to buy a new CD/DVD drive, those are cheap enough these days, but others who are good with tools might be able to take theirs apart, clean it inside and re-assemble it. 

Trying to force an installation or disk partitioning with a dirty CD/DVD drive can result in a corrupted partition table, just ask me, I know! :)

I recommend sticking with a good 'Parted based partitioner.  It could be that the Ubuntu CD is refusing to touch your partition because it is detecting something that's already in your partition table that it doesn't agree with. So by refusing to touch your MBR it is protecting you by failing on the safe side. Sometimes different disk partition editing programs have slightly different opinions about what is 'clean'. Things like exactly in which sector a partition should begin or end or the like can occasionally vary slightly between partition editors. If no 'Parted based partitioner will touch it, then it might be a feasible solution to try changing it a little with FDISK, but then again, back up your data first. FDISK might not have the fail-safe features that the 'Parted based partitioners use. Again, back up your data first.

Regards, Herman :)

---

