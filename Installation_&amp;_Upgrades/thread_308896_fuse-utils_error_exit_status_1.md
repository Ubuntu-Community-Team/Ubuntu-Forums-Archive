---
title: "fuse-utils: error exit status 1"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by Zyrshnikashnu on 2006-11-28
I'm trying to install fuse-utils so that I can use ntfs-3g and gmailfs. However, whenever I try to install the package, this is the output:
> Setting up fuse-utils (2.5.3-4.1) ...
creating fuse device node...
/sbin/MAKEDEV: don't know how to make device "fuse"
dpkG: error processing fuse-utils (--install):
 subprocess post-installation script returned error exit status 1
I've tried a few different versions of fuse-utils (though that doesn't look like the problem).

Any idea why MAKEDEV doesn't know how to make a fuse device?

---

