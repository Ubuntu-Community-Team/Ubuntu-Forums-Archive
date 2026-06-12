---
title: "postgres install problem"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by dsailer on 2008-01-19
having problems installing postgres, ubuntu 7.04:

apt-get install postgresql-8.2 postgresql-client-8.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postgresql-8.2 is already the newest version.
postgresql-client-8.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up postgresql-8.2 (8.2.6-0ubuntu0.7.04.1) ...
update-alternatives: unable to make /usr/share/postgresql/8.2/man/man1/pg_resetxlog.1.gz.dpkg-tmp a symlink to /etc/alternatives/pg_resetxlog.1.gz: No such file or directory
dpkg: error processing postgresql-8.2 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 postgresql-8.2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dsailer on 2008-01-22
bump

any ideas at all? I'll try anything (short of a reinstall of ubuntu)

---

### Post by dsailer on 2008-01-22
I tried removing the package (which succeeds) and re-installing, but get the same error. I also tried manually syncing the dirs/files related to postgres using a working box, but nothing changes, always the same error:

---

