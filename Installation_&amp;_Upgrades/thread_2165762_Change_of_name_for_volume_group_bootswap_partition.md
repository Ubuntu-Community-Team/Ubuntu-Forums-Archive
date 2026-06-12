---
title: "Change of name for volume group boot/swap partitions"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by frankerooney on 2013-08-06
Hi,
  I have LVM set up on 13.04 (from the default install). We use this machine, which is on vmware esxi for a template that we roll out to other machines. It's not a massive problem, but the original machine was named Ubuntu1304Template. The fstab entries and volume group names for LVM have this as their volume group name in the format e.g. Ubuntu1304Template-vg/swap.
I want to change the volume group name, which works ok via vgrename <old> <new>, and I've changed fstab to reflect the changes, however I'm thinking I need to update grub. Unfortunately grub complains with

/usr/sbin/grub-probe: error: failed to get canonical path of /dev/mapper/Ubuntu1304Template--vg-root

..So there's a reference to the previous volume group name somewhere, but I'm not sure where. Out of desperation I tried editing grub.cfg and running grub-install but I doubt that will work ok. Don't want to reboot in case it's all broken.
There's no reference under /etc/grub.d/* of the above, so where does it store this stuff, and how can I fix it?

I found reference to a similar operation where grub, not grub2 was used, but I'm still nervous to reboot, because the procedure is different.
[http://unixrevolution.blogspot.co.uk/2012/11/rename-your-root-vg-linux-lvm.html](http://unixrevolution.blogspot.co.uk/2012/11/rename-your-root-vg-linux-lvm.html)

Thanks
Andy

---

