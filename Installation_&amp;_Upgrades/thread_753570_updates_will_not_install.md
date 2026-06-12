---
title: "updates will not install"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by mattdasus900 on 2008-04-12
Hello, If anyone can help me with this I will be indebted to you.
I have Ubuntu install and I love it. The problem is when I try to do updates or install anything I get a message "Could not connect to 192.168.1.1:8080 (192.168.1.1), connection timed out".
I have a good network connection and I can connect to any site no problem. My routers IP is 192.168.1.1 but I have no idea why its telling my it cannot connect to that address.

For example I am trying to install compiz settings manager so I can have additional desktop effects and I get:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...buntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/...buntu2_all.deb)
Could not connect to 192.168.1.1:8080 (192.168.1.1), connection timed out

Any ideas?

---

### Post by Pumalite on 2008-04-12
Post:
ip addr

---

### Post by warp99 on 2008-04-13
> **mattdasus900 said:**
> Hello, If anyone can help me with this I will be indebted to you.
I have Ubuntu install and I love it. The problem is when I try to do updates or install anything I get a message "Could not connect to 192.168.1.1:8080 (192.168.1.1), connection timed out".
I have a good network connection and I can connect to any site no problem. My routers IP is 192.168.1.1 but I have no idea why its telling my it cannot connect to that address.

For example I am trying to install compiz settings manager so I can have additional desktop effects and I get:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...buntu2_all.deb](http://us.archive.ubuntu.com/ubuntu/...buntu2_all.deb)
Could not connect to 192.168.1.1:8080 (192.168.1.1), connection timed out

Any ideas?

It can't connect to port 8080. Can you ping the router? Are you running a proxy server?

---

