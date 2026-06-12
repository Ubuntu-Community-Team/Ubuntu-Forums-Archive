---
title: "Having trouble with ext3 partition on second hard drive"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by nighthawk3001 on 2007-12-31
I recently added a second hard drive to my computer. The primary hard drive was already a dual boot Ubuntu 7.04 and windows xp pro. I set up the second hard drive half with a ntfs partition to be used in windows and a ext3 partition to be used by Ubuntu. The partitions on the second hard drive are empty.

When I boot windows xp, it sees the second ntfs and it can read from it and it can write on it. But in Ubuntu, it sees the seconds ext3 partition, but it can only read from it. It won't let me write to it at all.

How do I get the second ext3 partition to read and write?

---

### Post by logos34 on 2007-12-31
here you go:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by taurus on 2007-12-31
You need to change the ownership of the mount point of that ext3 partition from root to your login name.  _Assuming_ it's mounted to /media/share and your login name is **nighthawk**, do

```
sudo chown -R **nighthawk**:**nighthawk** /media/share
ls -la /media
```

---

