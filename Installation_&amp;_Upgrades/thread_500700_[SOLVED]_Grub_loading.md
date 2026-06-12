---
title: "[SOLVED] Grub loading"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by upthelum on 2007-07-14
I have a dual-boot windows xp pro with ubuntu server but there are problems with windows so i must re-install windows as i cannot get a repair option. If i delete the windows partition then install windows will the boot grub be okay or will this pose me problems. Any other suggestions would be nice thanks.

---

### Post by bernied on 2007-07-14
windows doesn't play nice with other operating systems. when you reinstall it, it will wipe your master boot record (mbr) and only boot windows. 

The solution is to reinstall your mbr. You can do this either -
- by taking a copy of the mbr before you reinstall windows and writing it back when done (use the dd command for this - but be very careful)
- use you install disc or other live-cd to restore the grub mbr

It's always best to find out how to do this stuff before you reinstall windows, if the win install doesn't go well, you may be left witha  computer that cannot access the internet. live-cds are your friends.

---

### Post by upthelum on 2007-07-14
Thanks im back up and running again.

---

