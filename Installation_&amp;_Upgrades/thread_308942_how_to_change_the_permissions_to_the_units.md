---
title: "how to change the permissions to the units?"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by mogotocoro on 2006-11-28
Perticion /boot,/, /linux-swat and one installs ubuntu with one that /media/documentos call creates, but when I enter as usuary I do not have access to he himself, I cannot record, erase, I do not have permission for anything how it would do so that it can use it but like usuary way and not root, the permissions in the graphics mode are desabilitados, changes to him by console in chmod 777 /media/documentos and it does not pass anything, could help me? thanks

---

### Post by taurus on 2006-11-29
What filesystem is /media/documentos, ntfs or vfat?  I assume you mount it with /etc/fstab so paste a copy of your /etc/fstab here then.

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by mogotocoro on 2006-11-30
this in the format of linux ext3

---

### Post by taurus on 2006-11-30
So it is ext3 but I just want to see how you mount it!!!

---

