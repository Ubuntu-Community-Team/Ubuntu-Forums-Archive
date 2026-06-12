---
title: "Triple boot"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by JoeO on 2005-08-07
I thought I had a triple boot machine all set, but I do have a problem.

I have a single 160 GB drive with three partitions on it.  98SE on the first (C:), XP pro on the second (D:) and Ubunto on the third, or so it was.  At the very end of the initial install, I made the blunder of allowing Ubunto to put it's boot loader on C, remembering about time time I hit enter that that is where XP's MBR is, no matter where it is installed.  Obviously it wiped out XP's MBR so 98 and Ubunto would load, but not XP.  So I ran fdisk /mbr hoping that would fix XP's issue.  Not only didn't it fix XP's issue, then Ubunto wouldn't load either.

OK, 98 continues to work, so I reload XP Pro and it's working fine and I could see all of the partitions, NTFS, Fat 32, ext3 and swap. I installed XP on the NTFS partition and everything is as it should be. I did do a quick NTFS format of that partition before I installed the program.  After installation, I checked the partition table (from inside Windows) and nothing had changed.  Now 98 and XP are working.

Then, I go to re-install Ubunto - presumably on the same partition(s) as before, but no dice. It goes into the partition utility and the only selection I can get - under manual, guided, or anything else is for all 165GB of the one disk, and then only to partition the whole thing - PRI/LOG 163 GB Free space.

Nothing else. No partition table to select from as it exists inside windows, no ability to split the large hard disk; nothing - at least that I'm familiar with.

I'm really at a loss and could use the assistance.

Joe

---

### Post by Gezzer on 2005-08-07
[QUOTE=][/QUOTE]
 try a 9x boot floppy
use fdisk to delete the non dos partition that ubuntu created
reset that partition via fdisk then try another install with ubuntu ...

---

### Post by JoeO on 2005-08-07
I had thought about trying that, but I wasn't real confident in that when I couldn't see the FAT32 and the NTFS partitions either.

I'll let you know.

---

