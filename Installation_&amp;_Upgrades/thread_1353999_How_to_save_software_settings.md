---
title: "How to save software settings"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by ryy705 on 2009-12-13
Hello,

As I read through the various threads in this forum and I see that many Ubuntu veterans recommend backing up the home directory and installing the newest version of Ubuntu instead of upgrading.

I need Apache,MySQL,PHP installed on my computer for work.  I install them using the directions I found on kubuntuguide.org.  

If I do a clean install I will loose all my site settings and I will have to find and install all the extensions again.

Is there a way to avoid this?  Ubuntu server admins must face this problem on a regular basis.  So I am hoping that someone has come up with a semi painless procedure.  Could you kindly share the solution?

Many thanks for reading my post.

---

### Post by laceration on 2009-12-13
I too want to do a fresh install and have AMP installed for Web development.  I also have a ton of notes and data in MYSQL databases.  MYSQL databases are not stored in $HOME, nor are Apache settings.

The config file for Apache is at /etc/apache2/apache2.conf. Additional configurations are stored in subdirectories of the /etc/apache2 directory such as /etc/apache2/mods-enabled (for Apache modules), /etc/apache2/sites-enabled (for virtual hosts), and /etc/apache2/conf.d.

Back these up, or even better backup all of /etc because you will backup /etc/php5/php.ini which you very likely would have altered from the default.  There are also other php config files there to consider.

I keep my webpages in $HOME/public_html but they can also be kept in /var.

If you, like me, have MYSQL dbs, you need to back them up into tar.gz files and restore them after your new install.  The easiest way to do this is using Mysqladmin but you can also do it from the cli with mysqldump.
```
$mysqldump --all-databases | gzip >databasebackup.sql.gz
```
There is a good tutorial on using mysqldump at [http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database](http://www.devshed.com/c/a/MySQL/Backing-up-and-restoring-your-MySQL-Database)

Also go into synaptic and do search on Apache and PHP and make a note on addtional modules you have installed.

Once I have my fresh install I will refer to [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-9.10-lamp) for install.

I am apprehensive about doing all this, so I would appreciate any comments or other ideas anyone has.

---

