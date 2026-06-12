---
title: "external USB hard drive not mounted automatically after reboot"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by johnnyrevell on 2007-12-20
I plugged in a USB external hard drive to my Gutsy server; sda1 popped up on the desktop automatically mounted under /media/disk

I made a directory /backups and added
/dev/sda1 /backups defaults 0 0 
to /etc/fstab

However, if I leave the driver attached, on reboot the disk is not automatically mounted

If I issue sudo mount -a from the command line, it is then mounted into /backups

Is fstab read before USB drives are intialised of am I missing something?

Thanks

John

---

### Post by lespaul_rentals on 2007-12-20
> **johnnyrevell said:**
> I plugged in a USB external hard drive to my Gutsy server; sda1 popped up on the desktop automatically mounted under /media/disk

I made a directory /backups and added
/dev/sda1 /backups defaults 0 0 
to /etc/fstab

However, if I leave the driver attached, on reboot the disk is not automatically mounted

If I issue sudo mount -a from the command line, it is then mounted into /backups

Is fstab read before USB drives are intialised of am I missing something?

Thanks

John

It should be formatted this way:

```
/dev/sda1 /backups auto rw,auto,user,sync 0 0
```

---

