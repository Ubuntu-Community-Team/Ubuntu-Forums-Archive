---
title: "phpmyadmin installation problem"
date: 2017-02-12
forum: Installation &amp; Upgrades
---

### Post by zizu10 on 2017-02-12
i was try to install phpmyadmin and my pc has restart now when I try to install phpmyadmin again i got this error:

root@ubuntuPC:/home/zizu10# sudo apt-get install phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phpmyadmin is already the newest version (4:4.5.4.1-2ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 24 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up phpmyadmin (4:4.5.4.1-2ubuntu2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package phpmyadmin (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntuPC:/home/zizu10#


is there any fix for this?

---

### Post by darkaten1 on 2017-02-12
First I would highly recommend that you not be logged in as root but rather log in with your user account and just use the sudo command.

I think the issue is that another process has locked that file. Try killing that process. To find out what process is locking the file use fuser add the -k option to kill the process:

```
sudo fuser -v -k [COLOR=#000000]/var/cache/debconf/config.dat[/COLOR]
```

This maybe overkill but I would then purge phpmyadmin:

```
sudo apt purge phpmyadmin
```

Then attempt the install again.

---

