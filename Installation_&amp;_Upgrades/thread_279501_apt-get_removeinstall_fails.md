---
title: "apt-get remove/install fails"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by mwerlberger on 2006-10-18
I wanted to change from dovecot to cyrus imap. removed dovecot and installed courier. but:

apt-get install courier-authdaemon courier-authmysql courier-pop courier-pop-ssl courier-imap courier-imap-ssl

returns with

```

Reading package lists... Done
Building dependency tree... Done
courier-authdaemon is already the newest version.
courier-authmysql is already the newest version.
courier-pop is already the newest version.
courier-pop-ssl is already the newest version.
courier-imap is already the newest version.
courier-imap-ssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up courier-authdaemon (0.47-13ubuntu5.1) ...
 * Starting Courier authdaemon...
/usr/lib/courier/authlib/authdaemond: line 24: /etc/courier/authdaemonrc: No such file or directory
   ...fail!
invoke-rc.d: initscript courier-authdaemon, action "start" failed.
dpkg: error processing courier-authdaemon (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of courier-authmysql:
 courier-authmysql depends on courier-authdaemon (>= 0.47); however:
  Package courier-authdaemon is not configured yet.
dpkg: error processing courier-authmysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of courier-pop:
 courier-pop depends on courier-authdaemon (>= 0.47); however:
  Package courier-authdaemon is not configured yet.
dpkg: error processing courier-pop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of courier-pop-ssl:
 courier-pop-ssl depends on courier-pop; however:
  Package courier-pop is not configured yet.
dpkg: error processing courier-pop-ssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of courier-imap:
 courier-imap depends on courier-authdaemon (>= 0.47); however:
  Package courier-authdaemon is not configured yet.
dpkg: error processing courier-imap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of courier-imap-ssl:
 courier-imap-ssl depends on courier-imap (>= 1.3.7-3); however:
  Package courier-imap is not configured yet.
dpkg: error processing courier-imap-ssl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 courier-authdaemon
 courier-authmysql
 courier-pop
 courier-pop-ssl
 courier-imap
 courier-imap-ssl
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

ok i thought about just reinstalling but
 apt-get remove courier-authdaemon courier-authmysql courier-pop courier-pop-ssl courier-imap courier-imap-ssl
```

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  courier-authdaemon courier-authmysql courier-imap courier-imap-ssl courier-pop courier-pop-ssl
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 4674kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 25222 files and directories currently installed.)
Removing courier-pop-ssl ...
Removing courier-pop ...
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "stop" failed.
dpkg: error processing courier-pop (--remove):
 subprocess pre-removal script returned error exit status 1
 * ERR: config file missing
invoke-rc.d: initscript courier-pop, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing courier-imap-ssl ...
Removing courier-imap ...
 * ERR: config file missing
invoke-rc.d: initscript courier-imap, action "stop" failed.
dpkg: error processing courier-imap (--remove):
 subprocess pre-removal script returned error exit status 1
Removing courier-authmysql ...
Removing courier-authdaemon ...
 * Stopping Courier authdaemon...
/usr/lib/courier/authlib/authdaemond: line 24: /etc/courier/authdaemonrc: No such file or directory
   ...fail!
invoke-rc.d: initscript courier-authdaemon, action "stop" failed.
dpkg: error processing courier-authdaemon (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 courier-pop
 courier-imap
 courier-authdaemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

please give me some hint how i can solve that problem....

Regards,
 Manuel

---

### Post by mwerlberger on 2006-10-18
Damn. Just figured the problem out the second after i posted. The thing was that i hat been testing some configs and moved /etc/courier away. Moving it back fixed the problem. Sorry to bother you....

---

