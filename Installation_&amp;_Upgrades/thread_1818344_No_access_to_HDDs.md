---
title: "No access to HDDs"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by aSystemOverload on 2011-08-04
Hi

Recently installed Ubuntu, I've got 2 * 500GB HDDs, mounted and partitioned, but I don't have read/write access to them, only root does.. How can i get access to save files and create folders etc?!?!?

thnx

---

### Post by gordintoronto on 2011-08-04
Re-install Ubuntu. Create a "root" (/) partition, a /home partition and a small swap partition on one hard drive. Worry about the other drive later.

---

### Post by pjd99 on 2011-08-04
Can you please post the contents of /etc/fstab, it sounds like you need to modify the mount options so regular users have full access.

```

cat /etc/fstab

```and also can you post the output of:
```

ls -la /dev/disk/by-uuid/

```

EDIT:
and the output of:
```

sudo fdisk -l

```

---

