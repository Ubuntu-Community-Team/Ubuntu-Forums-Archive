---
title: "/home partition displaced"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by Xswitch on 2008-06-07
Had to upgrade using CD.  Forgot to write down UUID for /etc/fstab.  

**How do I get my /home partion back in fstab so that everything goes back to normal again?**

Thanks...

---

### Post by dstew on 2008-06-07
From the Live CD, do the command fdisk -l to list your hard disk partitions. Identify your /home partition. You can edit your /etc/fstab file and use the device name, like /dev/sda2. If you prefer, you can use the UUID. Get it using the command```
sudo vol_id /dev/sda2
```

---

### Post by Xswitch on 2008-06-07
Thanks dstew...  Much appreciated...

---

