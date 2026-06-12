---
title: "Samba fails after upgrade from 10.04 to 12.04"
date: 2012-08-19
forum: Installation &amp; Upgrades
---

### Post by oehq on 2012-08-19
I just upgraded from 10.04 to 12.04 and now the samba install fails generating the following error

Any ideas on how to solve??

***************************************************
heffsvr2@heffsvr-2:~$ sudo apt-get install samba4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdesudo libdb4.8 update-manager-kde libgnome-desktop-2-17
Use 'apt-get autoremove' to remove them.
Suggested packages:
  phpldapadmin samba-gtk swat2
The following NEW packages will be installed:
  samba4
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,649 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Preconfiguring packages ...
Traceback (most recent call last):
  File "/usr/bin/samba-tool", line 26, in <module>
    from samba.netcmd.main import cmd_sambatool
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/main.py", line 24, in <module>
    from samba.netcmd.delegation import cmd_delegation
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/delegation.py", line 29, in <module>
    from samba.netcmd.common import _get_user_realm_domain
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/common.py", line 24, in <module>
    from samba.net import Net
ImportError: libkdc-policy.so: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/samba-tool", line 26, in <module>
    from samba.netcmd.main import cmd_sambatool
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/main.py", line 24, in <module>
    from samba.netcmd.delegation import cmd_delegation
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/delegation.py", line 29, in <module>
    from samba.netcmd.common import _get_user_realm_domain
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/common.py", line 24, in <module>
    from samba.net import Net
ImportError: libkdc-policy.so: cannot open shared object file: No such file or directory
Selecting previously unselected package samba4.
(Reading database ... 246689 files and directories currently installed.)
Unpacking samba4 (from .../samba4_4.0.0~alpha18.dfsg1-4ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "announce version"
Ignoring unknown parameter "announce version"
Unknown parameter encountered: "usershare owner only"
Ignoring unknown parameter "usershare owner only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "printing"
Ignoring unknown parameter "printing"
Unknown parameter encountered: "printcap name"
Ignoring unknown parameter "printcap name"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "syslog only"
Ignoring unknown parameter "syslog only"
Unknown parameter encountered: "admin users"
Ignoring unknown parameter "admin users"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "write list"
Ignoring unknown parameter "write list"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "announce version"
Ignoring unknown parameter "announce version"
Unknown parameter encountered: "usershare owner only"
Ignoring unknown parameter "usershare owner only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "printing"
Ignoring unknown parameter "printing"
Unknown parameter encountered: "printcap name"
Ignoring unknown parameter "printcap name"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "syslog only"
Ignoring unknown parameter "syslog only"
Unknown parameter encountered: "admin users"
Ignoring unknown parameter "admin users"
Unknown parameter encountered: "valid users"
Ignoring unknown parameter "valid users"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "write list"
Ignoring unknown parameter "write list"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "force user"
Ignoring unknown parameter "force user"
Unknown parameter encountered: "force group"
Ignoring unknown parameter "force group"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "guest only"
Ignoring unknown parameter "guest only"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
No apport report written because MaxReports is reached already
Errors were encountered while processing:

***************************************************

---

