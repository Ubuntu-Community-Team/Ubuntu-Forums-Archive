---
title: "can you increase the size of partions after install if there is a swapfile next to it"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by CraigGB on 2008-02-23
hi there,
           after my old hard drive killed itself ive started again, i made a 15gb partion and put the swap partion directly next to it so its sort of um trapped i went on gparted and found i cant expand it now, i was wondering if anyone can come up with ideas on how to expand it or is 15gb large enough i wont be using it for storing music or anything, im still gonna use vista as my main os (i like it) but it would be nice to have a larger partion as im leaning towards Ubuntu though i now use kde on it, also i would like to say this fourm is great as it has helped me lots before (hint hint):lolflag:

thanks

---

### Post by logos34 on 2008-02-23
15 gb should be plenty space from what you've said (you actually only need like 7 gb or so tops for root itself).  But if you want to expand it you can easily do so from the live cd by simply deleting the swap partition (along with the extended partition housing it, if that's the way it installed), resize root to the right, then create a new swap like the old (either inside an extended or a new primary)--that way the partition numbers will be retained (otherwise you'll have to edit /etc/fstab).

You might want to post your disk layout:

**sudo fdisk -l**

---

