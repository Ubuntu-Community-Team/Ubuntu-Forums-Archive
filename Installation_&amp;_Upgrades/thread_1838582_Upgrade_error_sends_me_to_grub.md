---
title: "Upgrade error sends me to grub"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by eckscalibur on 2011-09-03
I did an upgrade while in Wubi and either the laptop battery died or something went wrong with the upgrade process, but now when I boot to Ubuntu, grub can't find the OS.  I've gone through the usual steps of setting the kernel image directory as follows:

insmod ntfs
set root=(hd0,2)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2... (tab complete) root=/dev/sd...

...but no sd or hd is listed in the dev folder.  Not sure what the problem is.  Any ideas?

---

### Post by bcbc on 2011-09-03
If you ran out of space that would cause problems. If you had lost power as well.

Are you referring to an update or an actual upgrade? Upgrades are worse to recover from.

I would start by extracting data using e.g. [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

Then boot an Ubuntu CD in live CD mode (try it without installing) and [fsck]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") the root.disk

After that try mounting it (same link) and check the space (you're looking for /dev/loop#):
```
df -h
```

If you get it booting again, first boot in recover mode and fix packaging errors. Otherwise post back wherever you get to.

---

### Post by eckscalibur on 2011-09-03
An actual upgrade, from 9.10 to 11.04.

---

### Post by bcbc on 2011-09-03
Well, you'd have to upgrade first to 10.04 then to 10.10 and then to 11.04. There's no upgrade path from 9.10 direct to 11.04

Okay, well the same steps apply (might need to chroot to repair though). But get your data off the root.disk first. 

Once that's done - you might find it easier just to reinstall - upgrading 3 times in a row is a time-consuming process (even without errors). Might be a good idea to think about a direct dual boot (not wubi) as well.

---

