---
title: "OpenBSD file system"
date: 2005-02-04
forum: Installation &amp; Upgrades
---

### Post by mappler on 2005-02-04
This might be the wrong forum for this post (if so, I apologize..I couldn't decide on a better one). 

I have a machine now that is running OpenBSD.  I would like to convert this machine to Ubuntu.  However, it is currently holding a healthy amount of data that would be inconvenient to move around.  Can Ubuntu read OpenBSD disklabel partitions?

Thanks,
 -Matt

---

### Post by Juergen on 2005-02-05
Maybe this is also useful for OpenBSD:
[http://www.tldp.org/HOWTO/Linux+FreeBSD-5.html](http://www.tldp.org/HOWTO/Linux+FreeBSD-5.html) 

I can't get Ubuntu to work with my freeBSD, but maybe the kernel isn't configured for this, I haven't looked at the config so far.

It might be inconvenient, but I think the easiest would be to create a partition that both OSs can read/write and share the files via this partition. 
In freeBSD this would be formatted ext2, and I think openBSD also supports this fs.

---

