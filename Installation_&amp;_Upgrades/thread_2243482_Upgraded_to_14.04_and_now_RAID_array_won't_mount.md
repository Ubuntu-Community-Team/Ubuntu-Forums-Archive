---
title: "Upgraded to 14.04 and now RAID array won't mount"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by mgbridges on 2014-09-09
Hi,

I just upgraded to 14.04 and most things seem to work fine. However, my RAID1 array won't mount anymore.

Initially I thought that perhaps the software RAID hadn't recreated the array, but that checked out OK. I managed to track it down to a problem with the MOUNT.

The line in my fstab is:
/dev/md0    /media/fileshare  ext4    rw,user,auto,exec  0     0

When I ran this manually I got an error message. Looking in the syslog shows it to be:
EXT4-fs (md0):bad geometry: block count 244190000 exceeds size of device (244189984 blocks)

What can I do to mount my device without losing data?

I'm not a particular Ubuntu expert, so please be gentle with me!

Cheers,

Martin

---

### Post by mgbridges on 2014-10-04
Bumping this question - any ideas?

---

