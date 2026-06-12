---
title: "Unable to install MySQL - error on starting server"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Steax on 2008-02-24
I'm running Ubuntu Fiesty (unable to upgrade via web because 1gb is too hard on my web usage quota...), and have installed Apache/MySQL/PHP. It included a lot of stumbling around because I couldn't get a lot of it to work, but eventually it did. Then after using it for a while, MySQL doesn't work at all! It keeps failing.

So I try uninstalling everything starting with mysql in Synaptic. Every time I install, this comes up:

```

Setting up mysql-server-5.0 (5.0.38-0ubuntu1.2) ...
 * Stopping MySQL database server mysqld                                                                                                [ OK ] 
 * Starting MySQL database server mysqld                                                                                                [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I've done it several times over. A complete reinstallation of Apache/PHP/MySQL would also be fine; I don't have much valuable data in there. Can someone please help?

Thanks!

(PS: I'm unsure as to which forum to place this in. Please move if I'm mistaken...)

---

### Post by whazooo on 2008-02-24
see here
[http://forums.vpslink.com/archive/index.php/t-797.html](http://forums.vpslink.com/archive/index.php/t-797.html)

or here
[http://ubuntuforums.org/showthread.php?t=339505&highlight=mysql-server-5.0](http://ubuntuforums.org/showthread.php?t=339505&highlight=mysql-server-5.0)

---

### Post by Steax on 2008-02-24
Thanks for the reply!

I've tried uncommenting skip-innodb in /etc/mysql/my.cnf, but it still doesn't work. I don't quite understand the second link, though... I still need it as localhost. Can you please explain?

---

