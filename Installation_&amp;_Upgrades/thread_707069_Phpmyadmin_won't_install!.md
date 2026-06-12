---
title: "Phpmyadmin won't install!"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by mlissner on 2008-02-25
I'm trying to set up my drupal installation to work with multisites, and to do so, I seem to need phpmyadmin. The problem is that when I install it, I get:```
sudo apt-get install  phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
phpmyadmin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up drupal-5.1 (5.1-0ubuntu2.3) ...
dbconfig-common: writing config to /etc/dbconfig-common/drupal-5.1.conf
Replacing config file /etc/drupal/5.1/sites/default/dbconfig.php with new version
dbconfig-common: flushing administrative password
dpkg: error processing drupal-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 drupal-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Any ideas on how to fix this?

---

### Post by keenboy on 2008-02-27
Looks as if an install or failed installation of drupal is causing this. Are you using drupal? If not I would uninstall it and try installing phpmyadmin.

---

### Post by az on 2008-02-27
I would suggest you install Drupal from upstream and not use the Ubuntu repositories for that.  Drupal has its own update-status module to help you manage third-party modules, something the Ubuntu package manager will not do.

So, to fix your problem, remove the Drupal package and install it from the drupal website.  It's quite easy to do.

I do recommend you continue to manage your LAMP stack using the package manager, of course.  Just don't use the package manager to manage web applications running on top of your LAMP server.

---

### Post by mlissner on 2008-02-27
Well, I'm quickly moving in that direction, but I'm of the if-it-ain't-broke thinking right now, and I do have a functional drupal install at the moment. I have the update-status module as of a few days ago, and yes, I need to do some updating. I guess that might be a good time to officially uninstall drupal from the repos, though I'm unsure what effects that might have on various server configuration settings...

It seems like the drupal tables in the mysql database must be causing this error,which makes me think that uninstalling drupal probably won't help the situation....unless perhaps I uninstall mysql too....

---

