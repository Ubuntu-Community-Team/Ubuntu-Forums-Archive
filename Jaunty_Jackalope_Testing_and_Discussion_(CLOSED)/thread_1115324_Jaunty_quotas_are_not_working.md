---
title: "Jaunty quotas are not working"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gecka on 2009-04-03
Hello,

I have setup my harddrive with LVM and ext4 partitions:

```
# fdisk -l

Disque /dev/sda: 749.9 Go, 749999226880 octets
255 têtes, 63 secteurs/piste, 91182 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Identifiant de disque : 0x00019812

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1       91151   732170376   8e  Linux LVM
/dev/sda2           91152       91182      249007+   5  Etendue
/dev/sda5           91152       91182      248976   83  Linux
```

But I can't enable quotas support:
```

# quotacheck -guv /
quotacheck: Mountpoint (or device) / not found or has no quota enabled.
```

Whereas the partition is well configured:
```

#mount -l
/dev/mapper/ubuntu--gecka-root on / type ext4 (rw,relatime,errors=remount-ro,grpquota,usrquota) []
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
```

---

### Post by gecka on 2009-04-03
up...

---

