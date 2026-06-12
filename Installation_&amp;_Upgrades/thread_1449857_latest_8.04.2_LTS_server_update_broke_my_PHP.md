---
title: "latest 8.04.2 LTS server update broke my PHP"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by cgrandgent on 2010-04-08
See below for the relevant portions of the update log.
Note Apache would not start until I commented out the two "php_value" lines.

Afterwards, it's as if PHP is not configured for Apache.

I tried restoring my apache config files and also my php.ini, no luck.

   Chuck


    Update Packages     

Now updating apache2 ..

      Installing package(s) with command apt-get -y install apache2 ..

      Reading package lists...
      Building dependency tree...
      Reading state information...
      The following extra packages will be installed:
        apache2-mpm-worker apache2.2-common
      Suggested packages:
        apache2-doc
      The following packages will be REMOVED:
        apache2-mpm-prefork libapache2-mod-php5 mediawiki php5 php5-mysql
      The following NEW packages will be installed:
        apache2-mpm-worker
      The following packages will be upgraded:
        apache2 apache2.2-common
      2 upgraded, 1 newly installed, 5 to remove and 6 not upgraded.
      Need to get 1037kB of archives.
      After this operation, 25.4MB disk space will be freed.
      Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2 2.2.8-1ubuntu0.15 [46.0kB]
      Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2.2-common 2.2.8-1ubuntu0.15 [756kB]
      Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2-mpm-worker 2.2.8-1ubuntu0.15 [235kB]
      Fetched 1037kB in 3s (310kB/s)
      (Reading database ... 49734 files and directories currently installed.)
      Preparing to replace apache2 2.2.8-1ubuntu0.14 (using .../apache2_2.2.8-1ubuntu0.15_all.deb) ...
      Unpacking replacement apache2 ...
      (Reading database ... 49734 files and directories currently installed.)
      Removing mediawiki ...
      Removing php5 ...
      Removing php5-mysql ...
      Removing libapache2-mod-php5 ...
      Module php5 disabled; run /etc/init.d/apache2 force-reload to fully disable.
      Removing apache2-mpm-prefork ...
       * Stopping web server apache2
       * We failed to correctly shutdown apache, so we're now killing all running apache processes. This is almost certainly suboptimal, so please make sure your system is working as you'd expect now!
         ...done.
      (Reading database ... 48652 files and directories currently installed.)
      Preparing to replace apache2.2-common 2.2.8-1ubuntu0.14 (using .../apache2.2-common_2.2.8-1ubuntu0.15_i386.deb) ...
      Unpacking replacement apache2.2-common ...
      Selecting previously deselected package apache2-mpm-worker.
      Unpacking apache2-mpm-worker (from .../apache2-mpm-worker_2.2.8-1ubuntu0.15_i386.deb) ...
      Setting up apache2.2-common (2.2.8-1ubuntu0.15) ...

      Setting up apache2-mpm-worker (2.2.8-1ubuntu0.15) ...
       * Starting web server apache2
      Syntax error on line 69 of /etc/apache2/sites-enabled/ssl:
      Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
         ...fail!
      invoke-rc.d: initscript apache2, action "start" failed.

      Setting up apache2 (2.2.8-1ubuntu0.15) ...

      .. install complete.


Now updating apache2-mpm-prefork ..

      Installing package(s) with command apt-get -y install apache2-mpm-prefork ..

      Reading package lists...
      Building dependency tree...
      Reading state information...
      The following packages will be REMOVED:
        apache2-mpm-worker
      The following NEW packages will be installed:
        apache2-mpm-prefork
      0 upgraded, 1 newly installed, 1 to remove and 7 not upgraded.
      Need to get 232kB of archives.
      After this operation, 8192B disk space will be freed.
      Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2-mpm-prefork 2.2.8-1ubuntu0.15 [232kB]
      Fetched 232kB in 1s (176kB/s)
      dpkg: apache2-mpm-worker: dependency problems, but removing anyway as you request:
       apache2 depends on apache2-mpm-worker (>= 2.2.8-1ubuntu0.15) | apache2-mpm-prefork (>= 2.2.8-1ubuntu0.15) | apache2-mpm-event (>= 2.2.8-1ubuntu0.15); however:
        Package apache2-mpm-worker is to be removed.
        Package apache2-mpm-prefork is not installed.
        Package apache2-mpm-event is not installed.
      (Reading database ... 48661 files and directories currently installed.)
      Removing apache2-mpm-worker ...
       * Stopping web server apache2
         ...done.
      Selecting previously deselected package apache2-mpm-prefork.
      (Reading database ... 48652 files and directories currently installed.)
      Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.8-1ubuntu0.15_i386.deb) ...
      Setting up apache2-mpm-prefork (2.2.8-1ubuntu0.15) ...
       * Starting web server apache2
      Syntax error on line 69 of /etc/apache2/sites-enabled/ssl:
      Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
         ...fail!
      invoke-rc.d: initscript apache2, action "start" failed.


      .. install complete.


Now updating apache2-utils ..

      Installing package(s) with command apt-get -y install apache2-utils ..

      Reading package lists...
      Building dependency tree...
      Reading state information...
      The following packages will be upgraded:
        apache2-utils
      1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
      Need to get 141kB of archives.
      After this operation, 0B of additional disk space will be used.
      Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2-utils 2.2.8-1ubuntu0.15 [141kB]
      Fetched 141kB in 1s (134kB/s)
      (Reading database ... 48661 files and directories currently installed.)
      Preparing to replace apache2-utils 2.2.8-1ubuntu0.14 (using .../apache2-utils_2.2.8-1ubuntu0.15_i386.deb) ...
      Unpacking replacement apache2-utils ...
      Setting up apache2-utils (2.2.8-1ubuntu0.15) ...

      .. install complete.


Now updating mediawiki ..

      Installing package(s) with command apt-get -y install mediawiki ..

      Reading package lists...
      Building dependency tree...
      Reading state information...
      The following extra packages will be installed:
        libapache2-mod-php5 php5 php5-mysql
      Suggested packages:
        php-pear clamav mediawiki-math memcached php5-gd imagemagick
      Recommended packages:
        php5-cli
      The following NEW packages will be installed:
        libapache2-mod-php5 mediawiki php5 php5-mysql
      0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
      Need to get 4879kB/7417kB of archives.
      After this operation, 25.4MB of additional disk space will be used.
      Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe mediawiki 1:1.11.2-2ubuntu0.4 [4879kB]
      Preconfiguring packages ...
      Fetched 4879kB in 14s (334kB/s)
      Selecting previously deselected package libapache2-mod-php5.
      (Reading database ... 48661 files and directories currently installed.)
      Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.4-2ubuntu5.10_i386.deb) ...
      Selecting previously deselected package php5.
      Unpacking php5 (from .../php5_5.2.4-2ubuntu5.10_all.deb) ...
      Selecting previously deselected package php5-mysql.
      Unpacking php5-mysql (from .../php5-mysql_5.2.4-2ubuntu5.10_i386.deb) ...
      Selecting previously deselected package mediawiki.
      Unpacking mediawiki (from .../mediawiki_1%3a1.11.2-2ubuntu0.4_all.deb) ...
      Setting up libapache2-mod-php5 (5.2.4-2ubuntu5.10) ...

      Setting up php5 (5.2.4-2ubuntu5.10) ...
      Setting up php5-mysql (5.2.4-2ubuntu5.10) ...

      Setting up mediawiki (1:1.11.2-2ubuntu0.4) ...


      .. install complete.

---

### Post by cgrandgent on 2010-04-08
Well, I am almost back to normal.

The update DID leave PHP5 disabled.

But other changes were also needed:

1) Mediawiki - I had to restore the LocalSettings.php I had before
2) Flyspray - apparently aftert he update, Apache2's setting for being able to recognize an index.php (instead of index.html) had been reset.

---

### Post by tamone on 2012-06-04
Same for me.

I upgraded Ubuntu 8.04 and it broke my apache2+php5.

In fact I had an apache2-mpm-worker installed before.

First I read in php5 readme that I should use apache prefork instead. I tried to remove apache worker, but it asked me if it was ok to remove mediawiki too, which I did not want.

Then I found this error launching apache on the command line, about not finding /usr/lib/apache2/modules/libphp5.so.

I then apt-get install libapache2-mod-php5 which contains the libphp5.so and it worked then on.

I have no traces, but I believe that before the upgrade of apache2-mpm-worker+php5, the mode linking apache2 to php5 was different than after the switch to apache2-mpm-prefork. 

An other possible solution: Windependence ([http://ubuntuforums.org/archive/index.php/t-1631913.html](http://ubuntuforums.org/archive/index.php/t-1631913.html)) mention to remove completely php5 and reinstall:

"sudo apt-get --purge remove php5 php5-common php5-cli php5-gd
Then reinstall php5:

sudo apt-get install php5 php5-common php5-cli php5-gd"

Cheers

---

