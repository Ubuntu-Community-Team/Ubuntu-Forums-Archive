---
title: "upgrade from dapper almost went well...package screwing me up tho"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by hypermegachi on 2006-12-18
```

root@hostname:/var/cache/apt/archives# dpkg --force-all -r lighttpd
(Reading database ... 23233 files and directories currently installed.)
Removing lighttpd ...
/usr/sbin/invoke-rc.d: line 274: /sbin/runlevel: No such file or directory
 * Stopping web server lighttpd                                                                                       [fail] 
invoke-rc.d: initscript lighttpd, action "stop" failed.
dpkg: error processing lighttpd (--remove):
 subprocess pre-removal script returned error exit status 1
/usr/sbin/invoke-rc.d: line 274: /sbin/runlevel: No such file or directory
 * Starting web server lighttpd                                                                                       [ ok ] 
Errors were encountered while processing:
 lighttpd

```

even that didn't work!!!

---

