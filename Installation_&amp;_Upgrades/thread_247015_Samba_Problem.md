---
title: "Samba Problem"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by bryan4134 on 2006-08-30
Upgrading from 5.10 to 6.06

Mostly working but I keep getting this error:

Setting up libtheora0 (0.0.0.alpha7-1ubuntu1~dapper1) ...

Errors were encountered while processing:
samba
samba-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
subprocess post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of samba-dbg:
samba-dbg depends on samba (= 3.0.22-1ubuntu3.1); however:
Package samba is not configured yet.
dpkg: error processing samba-dbg (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
samba
samba-dbg

Any help appreciated. Thanks, Bryan

---

