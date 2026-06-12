---
title: "Add old SATA drive with Data"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by quantumstitch on 2008-11-29
Hi All,
I installed 32-bit Ubuntu a while back. I have lots of data (photos, movies, documents, etc.) on a second HDD. I would like to remove this second HDD and install a 64 bit linux distro on the boot drive (which has nothing but / and the home directories - already backed up on the second drive). Can I simply unplug the second, perform the install and then remount the second drive after the install? It is using the ext3 filesystem. Please advise.

Here's the output of df -hT

```
/dev/sda1     ext3    457G  202G  233G  47% /
tmpfs        tmpfs   1012M     0 1012M   0% /lib/init/rw
varrun       tmpfs   1012M  328K 1012M   1% /var/run
varlock      tmpfs   1012M     0 1012M   0% /var/lock
udev         tmpfs   1012M  2.8M 1009M   1% /dev
tmpfs        tmpfs   1012M   12K 1012M   1% /dev/shm
lrm          tmpfs   1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb1     ext3    463G  337G  102G  77% /storage
```

Thanks for any help.
-stitch

---

### Post by taurus on 2008-11-29
Yes.  However, you don't have to unplug the second harddrive.  Just tell the installer to install it on the first harddrive and mount the second harddrive somewhere.  Just remember not to format the second harddrive or your data on it will be erased.  But if you want to feel safe, unplug the second harddrive before you install if you wish.  Then, you can just reconnect it and add an entry in /etc/fstab to mount it automatically each time you boot.

---

### Post by quantumstitch on 2008-11-29
Thanks a bunch. I figured I could do that but I just wanted to be sure.

---

