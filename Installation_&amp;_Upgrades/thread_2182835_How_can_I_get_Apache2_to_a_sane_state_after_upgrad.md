---
title: "How can I get Apache2 to a sane state after upgrading from Raring to Saucy?"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by jonathanhayward on 2013-10-22
I've upgraded from Raring to Saucy and Apache2 is dead:

```
# apachectl restart
httpd not running, trying to start
no listening sockets available, shutting down
AH00015: Unable to open logs
Action 'restart' failed.
The Apache error log may have more information.
```

How can I get Apache back and running?

---

### Post by TheFu on 2013-10-22
I believe the new release uses apache 2.4, not 2.2. Perhaps that will help your troubleshooting?
Also - "unable to open logs" could mean that log file permissions aren't correct.

I'm waiting until 14.04 LTS, so no first-hand knowledge of the new apache.

---

