---
title: "Can't install Samba 4 in Ubuntu 11.10"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by loren41 on 2011-10-24
Upgraded to 11.10 from 11.04.  No longer connected to my Windows 7 server.  Reinstall of Samba 4 returned the following error details.  Looks like I am missing a parameter file somewhere.  Please help.

PACKAGE OPERATION FAILED
Errors were encountered while processing: 
 samba4 
Setting up samba4 (4.0.0~alpha17~git20110807.dfsg1-1ubuntu1) ... 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
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
Unknown parameter encountered: "username map" 
Ignoring unknown parameter "username map" 
Unknown parameter encountered: "writeable" 
Ignoring unknown parameter "writeable" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "writeable" 
Ignoring unknown parameter "writeable" 
Unknown parameter encountered: "valid users" 
Ignoring unknown parameter "valid users" 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
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
Unknown parameter encountered: "username map" 
Ignoring unknown parameter "username map" 
Unknown parameter encountered: "writeable" 
Ignoring unknown parameter "writeable" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "writeable" 
Ignoring unknown parameter "writeable" 
Unknown parameter encountered: "valid users" 
Ignoring unknown parameter "valid users" 
module samba_dsdb initialization failed : No such object 
Unable to load modules for /var/lib/samba/private/sam.ldb: dsdb_module_search_dn: did not find base dn @ROOTDSE (0 results) 
Traceback (most recent call last): 
  File "/usr/share/samba/setup/upgradeprovision", line 1716, in <module> 
    ldbs = get_ldbs(paths, creds, session, lp) 
  File "/usr/lib/pymodules/python2.7/samba/upgradehelpers.py", line 156, in get_ldbs 
    ldbs.sam = SamDB(paths.samdb, session_info=session, credentials=creds, lp=lp, options=["modules:samba_dsdb"]) 
  File "/usr/lib/pymodules/python2.7/samba/samdb.py", line 55, in __init__ 
    options=options) 
  File "/usr/lib/pymodules/python2.7/samba/__init__.py", line 114, in __init__ 
    self.connect(url, flags, options) 
  File "/usr/lib/pymodules/python2.7/samba/samdb.py", line 69, in connect 
    options=options) 
_ldb.LdbError: (80, 'dsdb_module_search_dn: did not find base dn @ROOTDSE (0 results)') 
dpkg: error processing samba4 (--configure): 
 subprocess installed post-installation script returned error exit status 1

---

### Post by oman412 on 2011-10-25
+1 I'm having the same problem

---

### Post by dantee on 2011-10-26
i have the same issue after i upgraded from 11.04 to 11.10.

any updates about this issue yet?

---

### Post by dantee on 2011-10-26
i found a work around and somehow the error message went away.

[http://ubuntuforums.org/showthread.php?t=1776671&page=2](http://ubuntuforums.org/showthread.php?t=1776671&page=2)

i'm still puzzled why this has to happen though.

---

