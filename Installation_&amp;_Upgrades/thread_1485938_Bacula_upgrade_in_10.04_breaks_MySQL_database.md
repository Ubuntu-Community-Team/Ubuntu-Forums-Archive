---
title: "Bacula upgrade in 10.04 breaks MySQL database"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by togdon on 2010-05-17
The /usr/share/bacula-director/update_mysql_tables file included in 10.04 upgrades the database version from version 11 to 12. Prior to 10.04 the version of the database that shipped with Ubuntu was 10, so using the upgrade script that's included in 10.04 will destroy your Bacula installation. 

You can fix this if you've been performing regular catalog backups. You'll need to know several things before starting:

1. The name of your bacula-archive-device-name. Look for the section that contains Media Type = File-CatalogBackup in /etc/bacula/bacula-sd.conf file, there you'll find both the name of the device as well as the path to the device (assuming that you backup to disk, if you backup to tape you'll find the name of the tape library I believe).

2. The name of the most recent catalog backup, if you're backing up to disk this is the most recent file in the path you found in above, if you're backing up to tape I believe you should just pop in the most recent one.

For the purposes of this we'll assuming that my device is FileStorage-CatalogBackup and that the most recent Volume is CatalogVolume-1234

```
sudo bextract FileStorage-CatalogBackup -V CatalogVolume-1234 /tmp
sudo chown -R `whoami` /tmp/var/
mysqladmin -u root -p drop bacula
mysqladmin -u root -p create bacula
mysql -u root -p bacula < /tmp/var/lib/bacula/bacula.sql
mysql -u root -p bacula -e 'SELECT * FROM Version;'
```

I'm guessing that you'll get back a VersionId of 10 from the last command, which is what I got... If you got something different back you'll need to run additional upgrades. I extracted the two that I've attached from the 5.0.2 sources, you should be able to pull them down from the bacula.org site if needed.

```
./update_mysql_tables_10_to_11 -u root -p
./update_mysql_tables_11_to_12 -u root -p
```

Hopefully this helps someone else.

---

