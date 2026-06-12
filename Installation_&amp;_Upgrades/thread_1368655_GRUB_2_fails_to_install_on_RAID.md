---
title: "GRUB 2 fails to install on RAID"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Jekshadow on 2009-12-30
I tried several times, and GRUB just gives me the same generic error every time.

```
Executing 'grub-install /dev/md0' failed.
```

/dev/md0 is my RAID device. 

I was using RAID 5 on four 36.4GB SCSI drives.

[http://i.imgur.com/5048v.jpg](http://i.imgur.com/5048v.jpg)

EDIT: 3 of the drives were active, one was spare.

---

### Post by presence1960 on 2009-12-30
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by Jekshadow on 2009-12-31
> **presence1960 said:**
> [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

Ah, GRUB doesn't support RAID (other than 1), so /boot must be on an non-RAID partition/device. Thanks.

---

