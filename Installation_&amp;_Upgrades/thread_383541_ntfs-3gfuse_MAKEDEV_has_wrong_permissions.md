---
title: "ntfs-3g/fuse: MAKEDEV has wrong permissions"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by ^rooker on 2007-03-13
**[PROBLEM]**
I'm running Kubuntu Edgy on an AMD 64bit and I just wanted to install ntfs-3g.
This post is just to let others know that there's something wrong with the permissions of /sbin/MAKEDEV.

running "sudo apt-get install ntfs-3g" gives me this errormessage:

> creating fuse device...
/var/lib/dpkg/info/fuse-utils.postinst: line 9: ./MAKEDEV: Permission denied
dpkg: error processing fuse-utils (--configure):

The line failing in "fuse-utils.postinst" is:
> cd /dev; ./MAKEDEV fuse

but why?


**[SOLUTION]**
Because /dev/MAKEDEV is a symlink to /sbin/MAKEDEV - which (strange, strange...) had these permissions:
> -rw-rw-r-- 1 root root 52322 2006-07-21 04:08 /sbin/MAKEDEV

Since it's a script, supposed to be executable I did a
```
sudo chmod 754 /sbin/MAKEDEV
```

Running "sudo apt-get install fuse-utils" afterwards runs smoothly.

Any ideas what has caused MAKEDEV to have wrong permissions? That's almost a fresh install of Edgy 64bit I'm running here. Maybe someone else also has this problem?

---

