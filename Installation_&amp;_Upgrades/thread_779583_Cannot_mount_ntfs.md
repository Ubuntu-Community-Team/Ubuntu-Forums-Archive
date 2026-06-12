---
title: "Cannot mount ntfs"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by mzar on 2008-05-02
Hi,

I just finish install my box with ubuntu. I added ntfs-config to read my windows hdd. But i got error. Why?

[[IMG]http://img441.imageshack.us/img441/9343/ntfsconfighf5.th.png[/IMG]](http://img441.imageshack.us/my.php?image=ntfsconfighf5.png)

---

### Post by lemming465 on 2008-05-02
Check and see if it's already mounted for you somewhere under /media.  Ubuntu will tend to try to mount NTFS partitions automatically, and your error message makes it look like that's what is going on.

If you want it mounted somewhere else, you can change the mount point (second column) in /etc/fstab.  Be careful; editing mistakes in /etc/fstab are hard to recover from, so make a backup copy first.

---

### Post by tamoneya on 2008-05-02
first try what was suggested by lemming465 but if you cant seem to find where it is mounted to try the following in terminal.```
sudo umount /dev/sdb1
```Then try to mount it where you choose.

---

