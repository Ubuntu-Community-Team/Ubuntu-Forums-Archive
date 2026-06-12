---
title: "Modified LVM and unbootable system"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by WaterSoul on 2007-10-27
Hi.

I installed today a system using LVM and the alternate boot disc. It is configured as this :
/dev/sdb1 : boot (130MB) ext3
/dev/sdb2 : swap (6GB)
/dev/sdb3 : lvm ( 400GB )

lvm groups : Stuff
lvm volume : Home (400 GB)

/dev/Stuff/Home (400GB) ext3

then I wanted to add /dev/sda1 in the group, so I did
pvcreate /dev/sda1

/dev/sda1 is 273 GB

then, I did
vgextend Stuff /dev/sda1

then
lvextend -L+273G /dev/Stuff/Home

and I tried to umount my /home so I could resize the ext3 partition, but it wouldn't let me do so. So I decided to restart the system in recovery mode to get a root login and do it from there.

But surprise! it would boot anymore. it hangs on Running /scripts/local-bottom, it blank screen with a flashing _ in the top left corner. 

In recovery mode, it hangs and let me go to a  (raminitfs) prompt. I tried to remove the physical volume from my lvm array but it said it couldn't lock the file, as if it was mounted. I checked 'mount' and it wasn't.

Now I'm helpless about that. I can't access my stuff anymore and the system can't boot. If I boot Windows, it still sees the drive, but my Gentoo installation just can't show it to me anymore. That's pretty wierd.

If anyone would give me a hand, that'd be nice! Thanks!

---

