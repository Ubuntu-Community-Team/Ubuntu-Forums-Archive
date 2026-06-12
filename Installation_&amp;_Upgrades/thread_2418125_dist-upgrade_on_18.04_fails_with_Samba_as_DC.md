---
title: "dist-upgrade on 18.04 fails with Samba as DC"
date: 2019-05-02
forum: Installation &amp; Upgrades
---

### Post by arjenvandrie on 2019-05-02
Hi,

apt dist-upgrade tries to restart winbind and other samba daemons separately while samba config disallows it due to samba role as DC.

What is the best way to get around this?

apt dist-upgrade output snippets:

May 02 09:59:40 uat-dc01 systemd[1]: Starting Samba NMB Daemon...
May 02 09:59:40 uat-dc01 nmbd[2460]: [2019/05/02 09:59:40.639465,  0] ../source3/nmbd/nmbd.c:923(main)
May 02 09:59:40 uat-dc01 nmbd[2460]:   server role = 'active directory domain controller' not compatible with running nmbd standalone.
May 02 09:59:40 uat-dc01 nmbd[2460]:   You should start 'samba' instead, and it will control starting the internal nbt server
May 02 09:59:40 uat-dc01 systemd[1]: nmbd.service: Main process exited, code=exited, status=1/FAILURE
May 02 09:59:40 uat-dc01 systemd[1]: nmbd.service: Failed with result 'exit-code'.
May 02 09:59:40 uat-dc01 systemd[1]: Failed to start Samba NMB Daemon.
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of libnss-winbind:amd64:
 libnss-winbind:amd64 depends on winbind (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.9); however:
  Package winbind is not configured yet.

dpkg: error processing package libnss-winbind:amd64 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 winbind
 libpam-winbind:amd64
 samba
 libnss-winbind:amd64

Thanks and best regards,
Arjen.

---

### Post by Xian on 2019-05-02
What is the output of:

```
[SIZE=1][FONT=Monaco]systemctl status -l smbd.service[/FONT][/SIZE]
```

---

### Post by rsteinmetz70112 on 2019-05-03
Was this system ever used as a DC for a NT4 style domain?
It looks like some of the older stuff is trying to run and may need to be disabled or removed.

---

