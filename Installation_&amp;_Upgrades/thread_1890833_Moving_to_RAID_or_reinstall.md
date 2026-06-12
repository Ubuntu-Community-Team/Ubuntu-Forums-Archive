---
title: "Moving to RAID or reinstall"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by geekyhawkes on 2011-12-04
Hey guys/girls;

im planning on moving my xubuntu machine (11.04 at the moment) to using RAID 0 for my xubuntu with the /boot drive also containing a winxp install (for those times you just need windows, few and sad moments but they exist).

Can i migrate to RAID 0 without a full format and reinstall (which seems very windows) or is there a way i could get RAID working based on my current install?  The drives i am going to stripe are 250gb SATA both on the machine at the moment and I am planning on using a 40gb sata drive to hold the /boot and the windows xp install (might even try winxp 18gb win7 25gb and then 2gb for /boot / GRUB). 

If a reinstall is best then thats fine, i need to move to 11.10 anyway, just asking really.

Thanks.

---

### Post by darkod on 2011-12-04
If it was RAID1, it's possible. But for RAID0 I think not.
If I understand it correctly, the point is to first create the raid array, then copy your data.
In the case of raid0 you can't create a new array unless you have two new disks on top of the current one.
In the case of raid1 you can create a degraded array on the second disk, copy the system, and then join the first disk to the array.

You can also consider putting /boot on the main disks too, but it has to be outside the raid0 array. You could make small identical partitions on both disks, and do a software raid1 for /boot, then use the rest of the disks for software raid0.

You are aware of the risk for your data in raid0, right? If one disk goes you lose all the data.

---

### Post by geekyhawkes on 2011-12-06
i am aware of the risk with striping, but the way I see it is if my current hdd dies then I loose it all anyway so I'm hoping the stripe will give some extra performance. I keep anything I really need on dropbox/my has anyway so nothing ventured nothing gained.

---

