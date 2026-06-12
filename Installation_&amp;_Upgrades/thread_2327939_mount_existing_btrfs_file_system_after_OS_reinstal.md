---
title: "mount existing btrfs file system after OS reinstall"
date: 2016-06-15
forum: Installation &amp; Upgrades
---

### Post by Derek_Gentle on 2016-06-15
So I just had to replace the HD in my media server as it had exceeded it's life expectancy by a number of years and finally failed.  I've since reinstalled the OS (Ubuntu Server 14.04 LTS) and need to remount the btrfs file system that exists on the other drives. 

I've searched the great Oracle (google) and have found mostly how to set it up, not how to reintegrate an existing array after an OS reinstall.

Can anyone help or point in the right direction?

Thanks!

---

### Post by Skaperen on 2016-06-15
how many other drives?  how were they originally formatted?

---

### Post by Derek_Gentle on 2016-06-15
[FONT=arial]My original setup was as follows:

1 x WD RE3 250GB (died)
5 x WD Red 3TB (btrfs stripe)

All I've done is removed the dead RE3 and replaced it with a 30GB SSD.  I've installed btrfs-tools and the drives are seen:


[/FONT]```

root@Unimatrix01:/export# btrfs filesystem show
Label: none  uuid: 513c6773-7199-4770-a2c5-0da19ab8113d
        Total devices 5 FS bytes used 10.64TiB
        devid    1 size 2.73TiB used 2.13TiB path /dev/sda
        devid    2 size 2.73TiB used 2.13TiB path /dev/sdc
        devid    3 size 2.73TiB used 2.13TiB path /dev/sdd
        devid    4 size 2.73TiB used 2.13TiB path /dev/sdb
        devid    5 size 2.73TiB used 2.13TiB path /dev/sde

```

But I am not sure how to make them available again. I've found the make.btrfs command, but have not been able to verify that this will retain the existing data, or if it will make a NEW file system.

---

### Post by Skaperen on 2016-06-24
i think (i could be wrong) that *btrfs stripe* only cares about the device order.  have you tried to mount them read/only manually?  how was it set up on the previous system?  did you add it to [FONT=courier new]/etc/fstab[/FONT] or have a script to mount them?

---

