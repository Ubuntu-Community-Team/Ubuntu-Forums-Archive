---
title: "Is it safe to remove samb4?"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by Daan on 2011-10-11
Hi,

After upgrading to Ubuntu 11.04, whenever I upgrade, I get

```
root@schmauck:/home/daan# aptitude upgrade
The following partially installed packages will be configured:
  samba4 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH?
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb

Traceback (most recent call last):
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module>
    ldbs = get_ldbs(paths, creds, session, lp)
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect
    options=options)
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba4 (4.0.0~alpha15~git20110124.dfsg1-2ubuntu1) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ldb: unable to stat module /usr/lib/samba/ldb/modules/samba : No such file or directory
ldb: failed to initialise module /usr/lib/samba/ldb/modules/samba : Unavailable
ldb: failed to initialise module /usr/lib/samba/ldb/modules : Unavailable
WARNING: Module [samba_dsdb] not found - do you need to set LDB_MODULES_PATH?
Unable to load modules for /var/lib/samba/private/sam.ldb: Failed to load modules from: /usr/lib/samba/ldb

Traceback (most recent call last):
  File "/usr/share/samba/setup/upgradeprovision", line 1597, in <module>
    ldbs = get_ldbs(paths, creds, session, lp)
  File "/usr/lib/python2.7/dist-packages/samba/upgradehelpers.py", line 159, in get_ldbs
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"])
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 53, in __init__
    options=options)
  File "/usr/lib/python2.7/dist-packages/samba/__init__.py", line 110, in __init__
    self.connect(url, flags, options)
  File "/usr/lib/python2.7/dist-packages/samba/samdb.py", line 66, in connect
    options=options)
_ldb.LdbError: (80, 'Failed to load modules from: /usr/lib/samba/ldb\n')
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba4
                                         

```

If I remove samba4, it will also remove other packages:

```
root@schmauck:/home/daan# aptitude remove samba4
The following packages will be REMOVED:  
  ldb-tools{u} libasn1-8-heimdal{u} libdcerpc0{u} libgensec0{u} libgssapi2-heimdal{u} libhcrypto4-heimdal{u} libhdb9-heimdal{u} libheimbase1-heimdal{u} libheimntlm0-heimdal{u} 
  libhx509-5-heimdal{u} libkdc2-heimdal{u} libkrb5-26-heimdal{u} libldb1{u} libndr-standard0{u} libndr0{u} libregistry0{u} libroken18-heimdal{u} libsamba-hostconfig0{u} 
  libsamba-util0{u} libsamdb0{u} libtevent0{u} libwind0-heimdal{u} python-dnspython{u} python-ldb{u} python-samba{u} python-talloc{u} python-tdb{u} samba4 samba4-common-bin{u} 
0 packages upgraded, 0 newly installed, 29 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 34.2 MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

```

Will I break anything if I remove samba4?

---

### Post by vandamme on 2011-10-18
I hope not. Got the same problem...

---

### Post by Daan on 2011-10-19
I removed it, with all the stuff that is listed above. No problems have occurred that relate to this, I think.

---

