---
title: "Karmic var mount wierdness"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cac on 2009-09-21
Applied latest updates this morning, rebooted, and now df and mount report my var partition mounted to /dev/.var...  However /proc/mounts reports it correctly mounted as /var.  I'm thinking this is from the latest updates to udev.  Anyone else having this or something similar?

```

root@darth:~# blkid /dev/vg00/lv_var
/dev/vg00/lv_var: UUID="f7a2ecbc-34b6-40b0-94e1-6bbb97f16091" TYPE="ext4" 

root@darth:~# grep var /etc/fstab
# /dev/mapper/vg00-lv_var
UUID=f7a2ecbc-34b6-40b0-94e1-6bbb97f16091 /var ext4 relatime,defaults 0 2

root@darth:~# cat /proc/mounts |grep lv_var
/dev/mapper/vg00-lv_var /var ext4 rw,relatime,barrier=1,data=ordered 0 0

root@darth:~# mount |grep lv_var
/dev/mapper/vg00-lv_var on /dev/.var type ext4 (rw,relatime)

root@darth:~# df -h |grep lv_var
df: `/dev/.var': No such file or directory

```

---

### Post by klucas on 2009-09-21
Hi
The same problem with my kubuntu 9.10 !!!
Any help?

Thanks

---

### Post by cac on 2009-09-21
Looks like is other weirdness a foot with mountall and mounting during boot so I filed a bug report: [434172](https://bugs.launchpad.net/bugs/434172).

---

