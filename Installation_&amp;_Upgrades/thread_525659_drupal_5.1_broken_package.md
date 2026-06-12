---
title: "drupal 5.1 broken package"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by timseal on 2007-08-14
I tried to install drupal 5.1 but it appears to be broken.  Now it won't go away.  Every time I install/remove anything, I get the following:
```
Setting up drupal-5.1 (5.1-0ubuntu2) ...
dbconfig-common: writing config to /etc/dbconfig-common/drupal-5.1.conf
Replacing config file /etc/drupal/5.1/sites/default/dbconfig.php with new version
dbconfig-common: flushing administrative password
dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1

```
with this at the end:
```
Errors were encountered while processing:
 drupal-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

How can I uninstall drupal?

---

### Post by IcemanV9 on 2007-08-21
I have a same problem yesterday. It is not really broken. All you need to do is to set up your 'root' password for MySql.

```
mysql -u root
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('yourpassword');

```

Here's how to uninstall drupal.

```
sudo aptitude purge drupal-5.1
```

---

### Post by anantmishra on 2007-10-02
I set the password of mysql but it didn't help. Still getting the same error :-(

---

### Post by thk on 2007-10-16
I can confirm this is broken

---

