---
title: "Use of mdadm RAID Pauses Boot for 10 Minutes"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by greggooch on 2007-02-03
I freshly installed Edgy on my apartment server with a RocketRAID 404 card and am having a problem with what I believe to be my mdadm configuration.  After I mdadm --create my four 200GB HDs Ubuntu then takes 10-15 minutes to boot.  I have edited /boot/grub/menu.lst to give it a verbose bootup and have confirmed that it is hanging on the mdadm initialization.  This problem happens even if I don't have it in the /etc/fstab and have reformatted 3 times to verify that this is the problem.  I'd also like to note that I previously ran Windows without issue (not that I'm going back).  Also - there I am booting from a separate 250GB HD not in the 4 drive RAID5.

---

