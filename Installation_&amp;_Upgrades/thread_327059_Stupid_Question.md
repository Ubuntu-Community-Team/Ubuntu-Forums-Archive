---
title: "Stupid Question"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by aristotlewilde on 2006-12-28
So, I finally got my Edgy Install the way I want it, but I created an issue for myself.

I installed to a 20gb hard drive I had installed, but want to migrate to an 80gb I have lying around.  

Is it possibel to use gparted Live CD and make an exact copy of the 20gb drive so it will boot from that drive and I can remove the 20gb??

I can always do a fresh install, but as stated above, my system is setup just how I want it.

p.s.  I also have a 40gb drive in there, and only two slots for drives to plug in.  That's why I want to remove the 20gb.

---

### Post by bulldog on 2006-12-28
Should be possible,but you need to change the UUID in menu.lst and fstab according the new hdd partitions.
To find the UUID for your partitions```
ls /dev/disk/by-uuid -lh
```

---

### Post by aristotlewilde on 2006-12-28
decided to be smart about it and just keep the 20gb drive and swap my 40 with the 80.  

No need to create more work...

---

