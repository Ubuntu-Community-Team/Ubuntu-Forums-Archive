---
title: "Squid-deb-proxy broken 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by qwill on 2012-04-27
After upgrading an ubuntu server to 12.04;
all updates tentatives on the server and clients results in a "Failed to create host name resolver: Invalid host name".

the squid-deb-proxy service does not seems to start anymore; and the clients are not able to cope (before; they would just ignore the proxy if they did not find it).

Temporary solution is to remove the 30Autoproxy file in the /etc/apt.conf.d directory. then updates are going fin (without the proxy)

Anyone sharing the same experience ?

Have no clue whether its a parameter that was flushed by the upgrade or not, any suggestion welcomes !

Qwill

---

### Post by qwill on 2012-04-27
Solved : the new squid is more rigourous concerning the acl.
I had both .ubuntu.com and security.ubuntu.com in the same acl file, which was confusing squid while trying to establish directory trees.

Remmoving .ubuntu.com and leaving the subdomains (security.ubuntu.com) was the answer. 
squid-deb-proxy now working !:p

---

