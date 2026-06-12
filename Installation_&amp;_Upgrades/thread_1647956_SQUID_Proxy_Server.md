---
title: "SQUID Proxy Server"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-12-18
Hi all, I would like to install and manage SQUID Proxy Server using command line in Ubuntu 10.04 Server.
Any suggestion will be highly appreciated. Thanks in advance.

---

### Post by sikander3786 on 2010-12-18
Installation:

```
sudo apt-get install squid
```

Configuration:

```
sudo nano /etc/squid/squid.conf
```

Start/stop/restart Squid:

```
sudo service squid start
sudo service squid stop
sudo service squid restart
```

Reload the config file without restarting Squid:

```
sudo service squid reload
```

Some useful links:

[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)
[http://www.squid-cache.org/](http://www.squid-cache.org/)
[http://ubuntu4beginners.blogspot.com/2011/01/how-to-setup-transparent-proxy-with.html](http://ubuntu4beginners.blogspot.com/2011/01/how-to-setup-transparent-proxy-with.html)

---

