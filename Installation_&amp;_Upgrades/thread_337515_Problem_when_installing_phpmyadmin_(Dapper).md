---
title: "Problem when installing phpmyadmin (Dapper)"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by lzap on 2007-01-13
Hello, I am not able to install phpmyadmin:

```
# agi phpmyadmin
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  phpmyadmin
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/3601kB of archives.
After unpacking 14.1MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package phpmyadmin.
(Reading database ... 21973 files and directories currently installed.)
Unpacking phpmyadmin (from .../phpmyadmin_4%3a2.8.0.3-1_all.deb) ...
Setting up phpmyadmin (2.8.0.3-1) ...

Creating config file /etc/phpmyadmin/apache.conf with new version

Creating config file /etc/phpmyadmin/config.footer.inc.php with new version

Creating config file /etc/phpmyadmin/config.header.inc.php with new version

Creating config file /etc/phpmyadmin/config.inc.php with new version

Creating config file /etc/phpmyadmin/htaccess with new version
dpkg: error processing phpmyadmin (--configure):
 subprocess post-installation script returned error exit status 254
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried to uninstall it, to purge it... nothing helped. Whats wrong here?

---

