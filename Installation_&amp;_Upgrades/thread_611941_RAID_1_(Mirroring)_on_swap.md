---
title: "RAID 1 (Mirroring) on swap?"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2007-11-13
My swap is currently a RAID0 stripping device.  However, [http://tldp.org/HOWTO/Software-RAID-HOWTO-2.html#ss2.3](http://tldp.org/HOWTO/Software-RAID-HOWTO-2.html#ss2.3) says that there's no need to do this for swapping, as the kernel will swap if you add multiple swap  devices in /etc/fstab with the same priority.

It goes on to say that it is a good idea to have a Mirror Disk Linux software RAID1 mirroring for the swap file.  My question is if you have multiple swap devices in /etc/fstab with the same priority.  For example:
[INDENT]/dev/sda2       swap           swap    defaults,pri=1   0 0
/dev/sdb2       swap           swap    defaults,pri=1   0 0[/INDENT] if /dev/sda2 fails, will Linux continue running using /dev/sdb2?

Thanks,

David

---

### Post by rkillcrazy on 2007-11-13
I'm no linux guru per se` but I don't see a real advantage to mirroring the swap area.  Striping it may make sense 'cause you could get better performance that way.  After all, swap is supposedly only used when memory runs low.  If you're tapping into the swap area often, it's time to get more RAM anyway.  However, mirroring the swap area seems like a couple steps backwards as for one, you're now caching data on a drive which is slower than RAM to begin with and secondly, mirroring that cached data just takes up more time and gives no real advantages.  Like I said, I'm no linux expert but I am a Windows Admin and I'd never consider mirroring a Windows pagefile or the swap disk for an app like PhotoShop.

11-13-07
1435 EST

---

### Post by ddrichardson on 2007-11-13
I haven't heard of mirroring swap space, ever. Linux doesn't use it much now anyway. Go back ten years and you needed it to run X on most PCs.

There is no advantage in running a mirrored array for swap either, as the data isn't something to be recovered in the event of failure.

---

### Post by davidkahn on 2007-11-13
Do you use mdadm to stripe the swap file or just list multiple swap devices in /etc/fstab?

---

### Post by ddrichardson on 2007-11-13
I'd use mdadm but honestly cannot see why you would do

---

