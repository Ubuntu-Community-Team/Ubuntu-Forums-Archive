---
title: "Apache2 not starting"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by dsi_me on 2011-12-16
Hi

I am using Ubuntu 10.04.3 LTS Server.
I have various websites hosted on this server in Apache2. Today morning I installed all the updates using 
sudo apt-get upgrade
sudo apt-get update

After it got updated, i rebooted my system.
Afterwards, i noticed all my websites were down. I rebooted apache, but it showed the following error
```
 sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                             
apache2: Syntax error on line 204 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/mime.load: Cannot load /usr/lib/apache2/modules/mod_mime.so into server: libpthread.so.0$libc.so.6: cannot open shared object file: No such file or directory
 [fail]

```
I dont know whats wrong. i didnt do anything else.
Any help will be much appreciated.
Thanks

---

### Post by Lars Noodén on 2011-12-16
What is the error log telling?

```

tail /var/log/apache2/error.log

```

---

### Post by dsi_me on 2011-12-16
error log is not showing anything regarding to this error. It has few errors from 1 of my websites which I have fixed now. 

please suggest me something.

---

