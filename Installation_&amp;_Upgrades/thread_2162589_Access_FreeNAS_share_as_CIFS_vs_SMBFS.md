---
title: "Access FreeNAS share as CIFS vs SMBFS"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by alawson on 2013-07-15
Hi,

I've installed a couple of new 12.04.2 VMs recently and I'm having a strange problem accessing my NAS.

The new installs use CIFS instead of SMBFS to access the share, and the problem manifests as this in the syslog of the new builds;

```
CIFS VFS: Autodisabling the use of server inode numbers on \\server\share. This server doesn't seem to support them properly. Hardlinks will not be recognized on this mount. Consider mounting with the "noserverino" option to silence this message.
```

The relevant line in fstab now reads;
```
//server/share cifs username=uname,password=pword
```

Where before it read;
```
//server/share smbfs username=uname,password=pword,uid=1000,iocharset=utf8,codepage=unicode  0  0
```

The VMs are running under VMWare ESXi 5.1.0 and the share is hosted off a FreeNAS 8.3.0 server.
I would use NFS, except I have a couple of Windows boxes accessing the same share and don't want to mix the permissions, etc.

Any ideas what I might be doing wrong?

Thanks for your assistance.

---

