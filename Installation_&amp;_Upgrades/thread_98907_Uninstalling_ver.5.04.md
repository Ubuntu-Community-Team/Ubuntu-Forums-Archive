---
title: "Uninstalling ver.5.04"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by denvernative on 2005-12-04
:confused: After installing ver 5.04 i found its not for me. I have tryed 2 times before to uninstall 5.04. i get 5.04 removed but then on a reboot it still goes to grub i get error 22 ( i asume means cant find anything to load) . i tryed some of the soulutions i found here (1 was go to control pannel/adminasration manegment/componet managment/disk managment  do not have disk manegment).if i could find grub maybe i could just delete ?
i have an 
HP Pavilan a620n
amd proc. 2.2
1 meg ram
160gig hard drv. partitioned into 6 ntfs and one ext3 for 5.04

hope this is enough info
thanks denvernative aka john

---

### Post by bwog on 2005-12-04
I assume you want windows back? Go into rescue mode with the windows CD and do fixmbr (there are also options like fixboot, but it is best to know what you are doing, so check a windows tutorial).

That should work. If there are still problems come back here. There is no need to reinstall windows (although that would also write a new mbr).

---

### Post by denvernative on 2005-12-04
Thanks Bwog for the reply i failed to mention that i reinstalled 5.04 and now have a complete GRUB so i can run xp again. but still need to remove grub then 5.04 and reclaim that dixk space     still :confused:

---

### Post by bwog on 2005-12-04
In that case my answer above still applies. Is there something you do not understand?

You get the disk space back by formatting that partition in ntfs.

---

### Post by dmxubuntu on 2005-12-04
[QUOTE=denvernative]Thanks Bwog for the reply i failed to mention that i reinstalled 5.04 and now have a complete GRUB so i can run xp again. but still need to remove grub then 5.04 and reclaim that dixk space     still :confused:[/QUOTE]
If you have 6 NTFS partitions, I assume that Windows is on those.
If you have XP, load from the CD, choose the Recovery console, do a "fixmbr". This will let you boot under XP without Grub. The NTLDR will take over.

You might check to see if the "fixmbr" command is available without the recovery console being loaded. I think it is not.

Under XP, delete the ext2 or ext3 partitions and recover the space using the windows disk tools.

---

