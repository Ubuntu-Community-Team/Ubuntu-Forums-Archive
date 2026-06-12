---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by giolicious on 2012-06-28
I'm trying to remove:

```
sudo apt-get remove courier-imap courier-imap-ssl courier-pop courier-pop-ssl
```

and keep getting this errror messages:

[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  courier-imap courier-imap-ssl courier-pop courier-pop-ssl
0 upgraded, 0 newly installed, 4 to remove and 11 not upgraded.
4 not fully installed or removed.
After this operation, 1,102 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169959 files and directories currently installed.)
Removing courier-imap-ssl ...
 * Courier IMAP-SSL server: ERROR - /usr/sbin/couriertcpd missing
invoke-rc.d: initscript courier-imap-ssl, action "stop" failed.
dpkg: error processing courier-imap-ssl (--remove):
 subprocess installed pre-removal script returned error exit status 1
 * Courier IMAP-SSL server: ERROR - /usr/sbin/couriertcpd missing
invoke-rc.d: initscript courier-imap-ssl, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Removing courier-imap ...
 * Courier IMAP server: ERROR - /usr/sbin/couriertcpd missing
invoke-rc.d: initscript courier-imap, action "stop" failed.
dpkg: error processing courier-imap (--remove):
 subprocess installed pre-removal script returned error exit status 1
Removing courier-pop-ssl ...
 * ERR: /usr/sbin/couriertcpd missing
invoke-rc.d: initscript courier-pop-ssl, action "stop" failed.
dpkg: error processing courier-pop-ssl (--remove):
 subprocess installed pre-removal script returned error exit status 1
Removing courier-pop ...
 * ERR: /usr/sbin/couriertcpd missing
invoke-rc.d: initscript courier-pop, action "stop" failed.
dpkg: error processing courier-pop (--remove):
 subprocess installed pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 courier-imap-ssl
 courier-imap
 courier-pop-ssl
 courier-pop
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]


Any help?

---

### Post by dino99 on 2012-06-28
maybe it complain about something really missing

check it (/usr/sbin/couriertcpd) via nautilus

---

### Post by giolicious on 2012-06-29
> **dino99 said:**
> maybe it complain about something really missing

check it (/usr/sbin/couriertcpd) via nautilus

yes its missing. i tried creating a blank file with that name but i still get the same error.

---

