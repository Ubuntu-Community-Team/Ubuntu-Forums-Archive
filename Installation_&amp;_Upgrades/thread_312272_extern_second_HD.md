---
title: "extern second HD"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by macme on 2006-12-04
I put a removeble harddisk in my server, IDE, i want to use it for ftp en file server.
How to get access to the disk??

---

### Post by taurus on 2006-12-04
You first need to know the name of that harddrive and mount it before you can use it!  Paste the output of this command here...

```
sudo fdisk -l
```

---

### Post by macme on 2006-12-04
I'm a newbee, how to find out that??

---

### Post by taurus on 2006-12-04
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
And if you want to mount it each time you boot Ubuntu, then you need to modify your /etc/fstab to add an entry for it.

```
cat /etc/fstab
```

---

