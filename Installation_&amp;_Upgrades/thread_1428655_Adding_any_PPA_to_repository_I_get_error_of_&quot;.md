---
title: "Adding any PPA to repository I get error of &quot;keyserver time out&quot;"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by abcuser on 2010-03-13
Using Ubuntu 9.10 to add any PPA I always get error.
```
sudo add-apt-repository ppa:cybolic/ppa
```

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 79E3BFF61556818AFD15688E150BA781A5FF2BFC
gpg: requesting key A5FF2BFC from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


Is there any way to make this PPA work?
Thanks.

---

