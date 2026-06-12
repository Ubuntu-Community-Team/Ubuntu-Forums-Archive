---
title: "OpenSSH breaking upgrade?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by metalcoat on 2008-04-24
Went to upgrade to the beta now want to upgrade to release but I get this error
```
After this operation, 2388kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 156105 files and directories currently installed.)
Unpacking openssh-client (from .../openssh-client_1%3a4.7p1-8ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openssh-client_1%3a4.7p1-8ubuntu1_i386.deb (--unpack):
 unable to make backup link of `./usr/bin/ssh' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking openssh-server (from .../openssh-server_1%3a4.7p1-8ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openssh-server_1%3a4.7p1-8ubuntu1_i386.deb (--unpack):
 unable to make backup link of `./usr/sbin/sshd' before installing new version: Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-client_1%3a4.7p1-8ubuntu1_i386.deb
 /var/cache/apt/archives/openssh-server_1%3a4.7p1-8ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

??

---

