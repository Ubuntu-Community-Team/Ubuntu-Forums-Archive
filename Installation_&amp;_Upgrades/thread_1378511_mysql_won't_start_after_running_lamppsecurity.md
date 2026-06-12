---
title: "mysql won't start after running lampp/security"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by LumbeeNDN on 2010-01-11
Hey guys, nube to ubuntu, and mysql...the forum is great and helping alot! I have ubuntu 9.10, and installed the latest lampp with default options. Apache/Mysql/Proftpd would start and stop fine. I then did 

sudo /opt/lampp/lampp security
...which I got from here... [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410) Although I'm pretty sure I was never prompted for the mySQL password. At any rate, now mySQL will not start (Apache and ProFTP are OK). Where can I start debugging this? Where is the conf file for mySQL?  Thanx in advance...

---

### Post by LumbeeNDN on 2010-01-14
...just thought I'd follow up on this...the following command fixed it...

```
run > chown -R nobody.root /opt/lampp/var/mysql 
```

---

