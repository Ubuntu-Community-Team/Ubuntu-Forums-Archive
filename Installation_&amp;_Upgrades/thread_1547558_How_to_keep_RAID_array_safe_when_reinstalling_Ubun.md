---
title: "How to keep RAID array safe when reinstalling Ubuntu"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by ShiftyPowers on 2010-08-06
Hey all,

I currently have a nice HTPC setup that has been upgraded from distribution to distribution since 8.xx all the way up to 9.10 now.  I just moved to a new place and it feels like the right time to do a fresh install of 10.04 into the HTPC.

The problem is that I have a RAID 5 array in the system that has all my pictures, videos, music, etc.  This OS is installed in a separate drive that is not part of the RAID array (I have 4 drives in the system, 3 in the array, 1 for the OS).

My question is what is the general process I should follow to do:

1.  a fresh install of 10.04
2.  do #1 while at the same time not losing my array (don't think I would anyway).
3.  what to do after install to get the array back up and running and mounted.

Cheers!
Shifty

---

### Post by ronparent on 2010-08-07
A software raid using mdadm?

---

### Post by ShiftyPowers on 2010-08-08
yep sorry, should have said that.  yes, a software RAID using mdadm

---

### Post by ShiftyPowers on 2010-08-09
bumpety bumpy bump?

---

### Post by jacekk015 on 2010-08-10
1. Backup!!!
2. Reinstall OS on OS drive
3. Assemble RAID array
4. Edit /etc/mdadm/mdadm.conf [you can use that to add needed line on the end of the conf file]
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```5. Create mount point
6. Mount assembled array
5. Edit /etc/fstab [add mounted RAID details]


Most important is the first point ;)

---

