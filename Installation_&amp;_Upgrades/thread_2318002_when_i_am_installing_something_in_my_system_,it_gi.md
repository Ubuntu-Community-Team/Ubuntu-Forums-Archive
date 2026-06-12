---
title: "when i am installing something in my system ,it gives me this error plz help me"
date: 2016-03-22
forum: Installation &amp; Upgrades
---

### Post by kush3 on 2016-03-22
eading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up install-info (6.0.0.dfsg.1-3) ...
/usr/sbin/update-info-dir: 8: /etc/environment: Syntax error: Unterminated quoted string
dpkg: error processing package install-info (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by howefield on 2016-03-22
Can you post the output of ...

```
cat /etc/environment
```

---

### Post by kush3 on 2016-03-22
Output of cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
http_proxy="http://192.168.*.*:3128/"
https_proxy="https://192.168.*.*:3128/"
all_proxy=socks://192.168.*.*:3128/"
ftp_proxy="ftp://192.168.*.*:3128/"

---

