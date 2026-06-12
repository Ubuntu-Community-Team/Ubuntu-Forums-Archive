---
title: "Upgrade from 6.10 to 7.04: warning: could not initiate dbus"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by tuga on 2007-01-01
I am trying to upgrade from 6.10 to 7.04.
When I do ```
gksudo "update-manager -c -d"
```
the following error occurs:
warning: could not initiate dbus
extracting '/tmp/tmpkCRLCN/feisty.tar.gz'
authenticate '/tmp/tmpkCRLCN/feisty.tar.gz' against '/tmp/tmpkCRLCN/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
The content of /etc/apt/sources.list is:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted

Can anyone help?
Thanks

---

### Post by Sef on 2007-01-01
Since Fiesty is still alpha, the best way would be to use a cd to install.   Likely that is a bug that will be fixed in future updates.

---

