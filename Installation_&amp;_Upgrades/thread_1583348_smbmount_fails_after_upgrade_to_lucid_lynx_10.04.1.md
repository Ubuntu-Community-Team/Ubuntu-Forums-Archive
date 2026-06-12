---
title: "smbmount fails after upgrade to lucid lynx 10.04.1"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by gifford.scott on 2010-09-27
This fix is posted for anyone who finds that the samba smbmount command has started to fail after upgrading to ubuntu 10.04, lucid lynx.

Typical err scenario:

Under earlier ubuntu versions, smbmount worked and did not require user to be root.  Under ubuntu 10.04, smbmount now fails and appears to require superuser permissions.

$  smbmount //servername/shareloc localmount/
Password: 
mount error(1): Operation not permitted
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

$ sudo smbmount //servername/shareloc localmount/
Password: 
mount error(13): Permission denied


Fix:

/sbin/mount.cifs needs its setuid bit set, to allow regular users to execute the file successfully.  This change also has the positive effect of allowing smbmount to successfully complete...

$ sudo chmod +s /sbin/mount.cifs


regards,
gifford scott

---

