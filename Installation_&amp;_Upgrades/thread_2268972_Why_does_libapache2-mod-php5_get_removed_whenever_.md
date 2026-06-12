---
title: "Why does libapache2-mod-php5 get removed whenever I upgrade apache2?"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by MorningSleeper on 2015-03-12
I hope someone can help me figure out what is going on with my apache upgrades. For years, whenever I upgrade apache2, it tries to install apache2-mpm-itk even though I use the prefork module apache2-mpm-prefork and libapache2-mod-php5 is removed causing all my php files on my site to be downloaded thus exposing the php source code. Reinstalling libapache2-mod-php5 prevents the PHP files from being downloaded but of course I need to go change any passwords exposed in the files. Anyone know what is causing this? If related to apache2-mpm-itk trying to install each time, anyway to prevent it? It appears apache2-mpm-itk does not actually get installed when all done. The output of the apt-get install is below:
[COLOR=#000000]
[/COLOR]Module Index
Update Packages    
Now updating apache2 ..
Installing package(s) with command apt-get -y install apache2 ..
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  **apache2-mpm-itk** apache2.2-bin apache2.2-common
Suggested packages:
  apache2-suexec apache2-suexec-custom
**The following packages will be REMOVED:**
**  apache2-mpm-prefork libapache2-mod-php5**
**The following NEW packages will be installed:**
**  apache2-mpm-itk**
The following packages will be upgraded:
  apache2 apache2.2-bin apache2.2-common
3 upgraded, 1 newly installed, 2 to remove and 6 not upgraded.
Need to get 1574 kB of archives.
After this operation, 8714 kB disk space will be freed.
Get:1 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/main apache2 amd64 2.2.22-1ubuntu1.8 [1492 B]
Get:2 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/main apache2.2-bin amd64 2.2.22-1ubuntu1.8 [1344 kB]
Get:3 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/main apache2.2-common amd64 2.2.22-1ubuntu1.8 [226 kB]
Get:4 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/universe apache2-mpm-itk amd64 2.2.22-1ubuntu1.8 [2384 B]
Reading changelogs...
Get:1 Changelog for apache2.2-bin ([http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.8/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.8/changelog)) [151 kB]
apache2 (2.2.22-1ubuntu1.8) precise-security; urgency=medium


  * SECURITY UPDATE: HTTP header replacement via HTTP trailers (LP: #1425141)
    - debian/patches/CVE-2013-5704.patch: don't merge trailers by default
      and add a "MergeTrailers" directive to revert to previous behaviour
      to include/http_core.h, include/httpd.h, modules/http/http_filters.c,
      modules/http/http_request.c, modules/loggers/mod_log_config.c,
      modules/proxy/mod_proxy_http.c, modules/proxy/proxy_util.c,
      server/core.c, server/protocol.c.
    - CVE-2013-5704


 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Thu, 05 Mar 2015 12:40:00 -0500


apt-listchanges: Mailing root: apt-listchanges: changelogs for server1
Fetched 1574 kB in 3s (521 kB/s)
(Reading database ... 190291 files and directories currently installed.)
Preparing to replace apache2 2.2.22-1ubuntu1.7 (using .../apache2_2.2.22-1ubuntu1.8_amd64.deb) ...
Unpacking replacement apache2 ...
Preparing to replace apache2.2-bin 2.2.22-1ubuntu1.7 (using .../apache2.2-bin_2.2.22-1ubuntu1.8_amd64.deb) ...
Unpacking replacement apache2.2-bin ...
Preparing to replace apache2.2-common 2.2.22-1ubuntu1.7 (using .../apache2.2-common_2.2.22-1ubuntu1.8_amd64.deb) ...
Unpacking replacement apache2.2-common ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
**dpkg: apache2-mpm-prefork: dependency problems, but removing anyway as you requested:**
** libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:**
**  Package apache2-mpm-prefork is to be removed.**
**  Package apache2-mpm-itk is not installed.**
** libapache2-mod-cloudflare depends on apache2; however:**
**  Package apache2 is not configured yet.**
**  Package apache2-mpm-prefork which provides apache2 is to be removed.**
**(Reading database ... 190285 files and directories currently installed.)**
**Removing apache2-mpm-prefork ...**
 * Stopping web server apache2
 ... waiting    ...done.
Selecting previously unselected package apache2-mpm-itk.
(Reading database ... 190286 files and directories currently installed.)
Unpacking apache2-mpm-itk (from .../apache2-mpm-itk_2.2.22-1ubuntu1.8_amd64.deb) ...
Setting up apache2.2-bin (2.2.22-1ubuntu1.8) ...
Setting up apache2.2-common (2.2.22-1ubuntu1.8) ...
Setting up apache2-mpm-itk (2.2.22-1ubuntu1.8) ...
 * Starting web server apache2
   ...done.
(Reading database ... 190285 files and directories currently installed.)
**Removing libapache2-mod-php5 ...**
**Module php5 disabled.**
To activate the new configuration, you need to run:
  service apache2 restart
Setting up apache2 (2.2.22-1ubuntu1.8) ...
.. install complete.

---

### Post by SeijiSensei on 2015-03-12
Have you tried installing using [this method](https://help.ubuntu.com/community/ApacheMySQLPHP)?  Any different?

---

### Post by MorningSleeper on 2015-03-12
Thanks for the reply, the instructions on that page describe how I originally installed it couple years ago and it installed fine at that time. It is only since then whenever an upgrade has been released and I install it using apt-get -y install apache2 that it exhibits the described behavior.

 For whatever reason the upgrade process appears to try and remove apache2-mpm-prefork and install apache2-mpm-itk. Even though this never completes, libapache2-mod-php5 still gets removed towards the end - perhaps because it thinks apache2-mpm-prefork got uninstalled and thus is no longer needed. I wish I knew why it is trying to install apache2-mpm-itk which I don't use and trying to remove apache2-mpm-prefork which I do use as that seems to be the root of the problem.

---

### Post by SeijiSensei on 2015-03-12
I rarely upgrade individual packages and just use "sudo apt-get update; sudo apt-get upgrade" (or "dist-upgrade" if a new kernel is involved).

You might find this bug report helpful, even though it pertains to apache2-mpm-itk: [https://bugs.launchpad.net/ubuntu/+source/mpm-itk/+bug/1286882](https://bugs.launchpad.net/ubuntu/+source/mpm-itk/+bug/1286882).  It was the only thing I could find when searching for relevant bugs at Launchpad.

---

### Post by MorningSleeper on 2015-03-12
The log I posted was from upgrading within Webmin which updates individual packages although I have experienced the same behavior when using sudo apt-get update, sudo apt-get upgrade. I'll check that bug report.
 
I began thinking maybe it is trying to install apache2-mpm-itk because it detects it on my server but it does not appear to be installed.
 
ubuntu@server1:~$ sudo apt-get remove apache2-mpm-itk
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache2-mpm-itk is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 
I checked the cache and it appears.
 
ubuntu@server1:~$ sudo apt-cache search apache2-mpm-itk
apache2-mpm-itk - multiuser MPM for Apache 2.2
 
Tried to remove it from cache with
 
ubuntu@server1:~$ sudo apt-get clean
 
Then checked it again but it still finds it?
 
ubuntu@server1:~$ sudo apt-cache search apache2-mpm-itk
apache2-mpm-itk - multiuser MPM for Apache 2.2
 
Went to /var/cache/apt/archives but it is empty?

Also ran the following, does it mean libapache2-mod-php5 is dependent on apache2-mpm-itk and that is why apache2-mpm-itk tries to install?

ubuntu@server1:~$ sudo aptitude why apache2-mpm-itk
i   libapache2-mod-php5 Depends apache2-mpm-prefork (> 2.0.52) | apache2-mpm-itk

---

