---
title: "Updated - ZFS mount is now gone need"
date: 2014-07-07
forum: Installation &amp; Upgrades
---

### Post by mtweldon on 2014-07-07
Just did the normal update (13.1) and it did some ZFS updates and now my 4x3TB ZFS system is no longer mounted and zfs List shows nothing, unsure on what to do.
df -h isn't showing the drives in the list either.

---

### Post by mtweldon on 2014-07-07
sorry going to keep doing posts as I go along for myself and or potential others in the same situation or who might know how to resolve this.

Googled an error I was getting, found this would fix that error:

```
apt-get install --reinstall ubuntu-zfs

```

actually get a response now:

```
zpool status storage
  pool: storage
 state: ONLINE
  scan: none requested
config:

	NAME        STATE     READ WRITE CKSUM
	storage     ONLINE       0     0     0
	  raidz1-0  ONLINE       0     0     0
	    sdb     ONLINE       0     0     0
	    sdc     ONLINE       0     0     0
	    sdd     ONLINE       0     0     0
	    sde     ONLINE       0     0     0

```

now trying to figure out how to remount it

---

### Post by mtweldon on 2014-07-07
did a couple reboots and good to go now, freak out averted, this is why I absolutely hate doing updates / upgrades

---

