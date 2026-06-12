---
title: "No optical drive install?"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Baelari on 2008-03-02
There's no optical drive on the laptop I just ordered. What do I do to make an installation run without it? 

Lenovo X61 Tablet, if that's relevant.

---

### Post by overdrank on 2008-03-02
> **Baelari said:**
> There's no optical drive on the laptop I just ordered. What do I do to make an installation run without it? 

Lenovo X61 Tablet, if that's relevant.

HI and you can try this link for installing without a cd
[https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd](https://help.ubuntu.com/community/Installation#head-ca8e337bdfab6bfa1d064371898775fe1e9e22fd)
Also I do remember seeing several user with installation issues with that cpu "Intel's Santa Rosa mobile"
So you may search the forums for tips. and good luck!

---

### Post by Baelari on 2008-03-02
Exactly what I was looking for. Thanks!

---

### Post by Baelari on 2008-03-02
Seems like I've already run into a snag.

> Install syslinux:

*sudo aptitude install syslinux*

Insert the USB device you want to use for the installer. A few seconds after plugging in the USB device run the dmesg command or sudo fdisk -l to find device it was assigned. The rest of the instructions refer to /dev/sdX1, remember to replace X with your device location. 

installing syslinux was fine, but the */dev/sdX1* is my problem. "The rest of the instructions refer to /dev/sdX1" doesn't make much sense to me.

```
[ 3208.276000] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.4  PQ: 0 ANSI: 2
[ 3208.276000] sd 6:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[ 3208.280000] sd 6:0:0:0: [sdb] Write Protect is off
[ 3208.280000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3208.280000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3208.280000] sd 6:0:0:0: [sdb] 2001888 512-byte hardware sectors (1025 MB)
[ 3208.280000] sd 6:0:0:0: [sdb] Write Protect is off
[ 3208.280000] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3208.280000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3208.280000]  sdb: sdb1
[ 3208.284000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 3208.284000] sd 6:0:0:0: Attached scsi generic sg2 type 0
root@angie-laptop:~# /dev/sdb1
-bash: /dev/sdb1: Permission denied
root@angie-laptop:~# 

```

---

### Post by Baelari on 2008-03-02
I figured it out. It would be helpful if that mentioned you need to preface it with *syslinux -s*

---

