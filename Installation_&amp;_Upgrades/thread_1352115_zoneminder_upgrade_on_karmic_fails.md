---
title: "zoneminder upgrade on karmic fails"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by surfer63 on 2009-12-11
I was using zoneminder 1.23.3 on Ubuntu 9.04.
I upgraded to Karmic 9.10 and during the upgrade the zoneminder upgrade failed but it passed to quickly so I can't mention it here.

zoneminder 1.24.1 on Karmic doesn't work after the upgrade.
I removed zoneminder and autoremoved the dependencies. Than I tried to install zoneminder again using "sudo apt-get install zoneminder".

The following error is displayed:
```
Setting up zoneminder (1.24.1-1ubuntu2) ...
Undefined subroutine &ZoneMinder::Config::ZM_DB_NAME called at /usr/share/perl5/ZoneMinder/Config.pm line 89.
BEGIN failed--compilation aborted at /usr/share/perl5/ZoneMinder/Config.pm line 100.
Compilation failed in require at /usr/bin/zmupdate.pl line 49.
BEGIN failed--compilation aborted at /usr/bin/zmupdate.pl line 49.
dpkg: error processing zoneminder (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 zoneminder
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The zm database has been removed by the uninstall/upgrade process (I assume) and is not recreated.

The /etc/zm/zm.conf is empty.

I already installed/uninstalled several times.

---

### Post by surfer63 on 2009-12-11
Via a workaround it now works.
I manually created the database and gave the zmuser authorizations.
When installing the 1.24.1 again I received an update error on the zm_update-1.23.3.sql script. I emptied that script and ran the install again.
That functioned.

---

### Post by Pythaules on 2010-03-25
I have had this same problem, but I am not sure how Surfer63 said he fixed it.  Is there anyone out there that might be able to break this down for me.

---

### Post by Rrogers on 2010-04-14
Same here.  I would rather avoid a source build, but I am not familiar with creating databases and such.
Details for automatic installation would be appreciated.
Ray:confused:

---

### Post by surfer63 on 2010-06-11
Sorry, I have been off-line for a very long time.

When zoneminder is installed a lot of sql scripts are run by the installer. You can find them in "/usr/share/zoneminder/db/" like ```
/usr/share/zoneminder/db/zm_update-1.23.0.sql
/usr/share/zoneminder/db/zm_update-1.23.1.sql
/usr/share/zoneminder/db/zm_update-1.23.2.sql
/usr/share/zoneminder/db/zm_update-1.23.3.sql
/usr/share/zoneminder/db/zm_update-1.24.0.sql
/usr/share/zoneminder/db/zm_update-1.24.1.sql

```

So what I did is clearing the "/usr/share/zoneminder/db/zm_update-1.23.3.sql" using vi.
Then I rerun the installation as it won't download the package again and the installation finished correctly.

---

