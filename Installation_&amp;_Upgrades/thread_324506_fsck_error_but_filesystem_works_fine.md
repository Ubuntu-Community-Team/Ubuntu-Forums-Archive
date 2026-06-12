---
title: "fsck error but filesystem works fine"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by JacksonL on 2006-12-23
I'm using a single partition for the /home directory on two different ubuntu installations. both have the same username, uid, etc., that is: their entries are identical in /etc/passwd. when I boot into the second (most recently installed) installation it tells me that that /home partition has an error but if I ignore it I can boot into the system and it works perfectly as far as I can tell. any ideas how to fix this?

---

### Post by taurus on 2006-12-23
What does /etc/fstab (from the distro that complains about /home) look like then?

```
cat /etc/fstab
```

---

### Post by JacksonL on 2006-12-23
$cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ext3    defaults        0       2
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

sda1 is ubuntu-edgy, sda2 is /home, sda5 is swap
sdb1 is windowsXP, sdb2 is ubuntu-dapper (the complaining one)

---

### Post by taurus on 2006-12-23
> **JacksonL said:**
> $cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ext3    defaults        0       2
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

sda1 is ubuntu-edgy, sda2 is /home, sda5 is swap
sdb1 is windowsXP, sdb2 is ubuntu-dapper (the complaining one)

I think you meant /dev/sda3 is /home since there is no /dev/sda2!!!

I thought you said /home is the problem!!!

---

### Post by JacksonL on 2006-12-23
oy, yes. I'm sorry. that was a typo. /dev/sda3 is /home for both the dapper and edgy installations. it only gets an error when I'm turning on the computer, not when I'm actually using it. it works fine when I'm in either system. I'm using it right now.

---

### Post by taurus on 2006-12-23
What if you replace the last value from "2" to "1"?

```
/dev/sda3   /home   ext3   defaults   0   1
```

---

### Post by JacksonL on 2006-12-23
unfortunately that doesn't help. nothing changed

---

