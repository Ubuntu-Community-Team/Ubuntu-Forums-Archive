---
title: "Upgrade 10.04 to 10.10 fails with an incorrect low-diskspace message"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by bigred1 on 2011-09-21
I used the Upgrade Manager to upgrade 10.04 to 10.10. This fails on a diskspace error. See image attached. But I have plenty of free diskspace.

What do I need to do to upgrade?

See *df* report on diskspace  and *mount *output below:

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             9.2G  8.0G  729M  92% /
none                  997M  284K  997M   1% /dev
none                 1001M  2.3M  999M   1% /dev/shm
none                 1001M  348K 1001M   1% /var/run
none                 1001M     0 1001M   0% /var/lock
none                 1001M     0 1001M   0% /lib/init/rw
/dev/sdb3             132G   92G   34G  74% /home

```

Here is the meaning of *sdb1* and *sdb3*. 
```

$ mount |grep sdb
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
/dev/sdb3 on /home type ext4 (rw,user_xattr)
```

---

### Post by mue.de on 2011-09-21
As far as i see, you don't have 1.8GiB free on root-partition (sdb1) as requested by the install-routine.
I'm using now about 16 GB for '/' and it's nearly used up by kubuntu 10.04

mue.de

---

