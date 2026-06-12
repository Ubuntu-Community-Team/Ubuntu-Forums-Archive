---
title: "Why do I get the same error after every update/install/removal?!!"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2007-07-05
I've been seeing this a LOT!!!

```
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What's the story?

---

### Post by everythingsused on 2007-07-07
I was just having the same problem only with a different package. 

Running ```
sudo dpkg --configure -a
``` seems to have fixed it for me.

---

### Post by diablo75 on 2007-07-07
I'll give it a shot, thanks!

---

### Post by diablo75 on 2007-07-07
I tried the above command and here's what I got:

```
zeke@zeke-desktop:~$ sudo dpkg --configure -a
Password:
Setting up drupal-5.1 (5.1-0ubuntu2) ...
dbconfig-common: writing config to /etc/dbconfig-common/drupal-5.1.conf
Replacing config file /etc/drupal/5.1/sites/default/dbconfig.php with new version
dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 drupal-5.1
 clamav-base
zeke@zeke-desktop:~$ 
```

---

### Post by kitterma on 2007-07-12
Try sudo mkdir /var/run/clamav and then install again.

---

### Post by diablo75 on 2007-07-13
> **kitterma said:**
> Try sudo mkdir /var/run/clamav and then install again.

That helped a little.....

---

