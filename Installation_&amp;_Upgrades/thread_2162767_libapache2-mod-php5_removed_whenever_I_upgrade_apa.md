---
title: "libapache2-mod-php5 removed whenever I upgrade apache2"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by MorningSleeper on 2013-07-15
For the longest time, when I upgrade apache2, libapache2-mod-php5, is removed causing all my php files on my site to be downloaded thus exposing the php source code and installs apache2-mpm-itk even though I use the prefork module apache2-mpm-prefork. Reinstalling libapache2-mod-php5 returns things to normal but of course I need to go change any passwords exposed in the files. Anyone know how to prevent it from doing this each time? The output of the apt-get install and aptitude search apache2-mpm- is below:

========================
Now updating apache2 ..
Installing package(s) with command apt-get -y install apache2 ..
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-45-virtual linux-headers-3.2.0-45
  linux-headers-3.2.0-45-virtual
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  **apache2-mpm-itk** apache2.2-bin apache2.2-common
Suggested packages:
  apache2-suexec apache2-suexec-custom
[B]The following packages will be REMOVED:
  apache2-mpm-prefork libapache2-mod-php5
[/B][B]The following NEW packages will be installed:
  apache2-mpm-itk[/B]
The following packages will be upgraded:
  apache2 apache2.2-bin apache2.2-common
3 upgraded, 1 newly installed, 2 to remove and 13 not upgraded.
Need to get 1570 kB of archives.
After this operation, 8717 kB disk space will be freed.
Get:1 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/main apache2 amd64 2.2.22-1ubuntu1.4 [1492 B]
Get:2 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/main apache2.2-bin amd64 2.2.22-1ubuntu1.4 [1340 kB]
Get:3 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/main apache2.2-common amd64 2.2.22-1ubuntu1.4 [226 kB]
Get:4 [http://us-west-1.ec2.archive.ubuntu.com/ubuntu/](http://us-west-1.ec2.archive.ubuntu.com/ubuntu/) precise-updates/universe apache2-mpm-itk amd64 2.2.22-1ubuntu1.4 [2382 B]
Reading changelogs...
Get:1 Changelog for apache2.2-bin ([http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.4/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.22-1ubuntu1.4/changelog)) [148 kB]
apache2 (2.2.22-1ubuntu1.4) precise-security; urgency=low
 
  * SECURITY UPDATE: log file poisoning via mod_rewrite (LP: #1188069)
    - debian/patches/CVE-2013-1862.patch: properly escape items in
      modules/mappers/mod_rewrite.c.
    - CVE-2013-1862
  * SECURITY UPDATE: denial of service via MERGE request
    - debian/patches/CVE-2013-1896.patch: make sure DAV is enabled for URI
      in modules/dav/main/mod_dav.c.
    - CVE-2013-1896
 
-- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Fri, 12 Jul 2013 08:58:01 -0400
 
apt-listchanges: Mailing root: apt-listchanges: changelogs for server1
Fetched 1570 kB in 0s (2902 kB/s)
(Reading database ... 190162 files and directories currently installed.)
Preparing to replace apache2 2.2.22-1ubuntu1.3 (using .../apache2_2.2.22-1ubuntu1.4_amd64.deb) ...
Unpacking replacement apache2 ...
Preparing to replace apache2.2-bin 2.2.22-1ubuntu1.3 (using .../apache2.2-bin_2.2.22-1ubuntu1.4_amd64.deb) ...
Unpacking replacement apache2.2-bin ...
Preparing to replace apache2.2-common 2.2.22-1ubuntu1.3 (using .../apache2.2-common_2.2.22-1ubuntu1.4_amd64.deb) ...
Unpacking replacement apache2.2-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
[B]dpkg: apache2-mpm-prefork: dependency problems, but removing anyway as you requested:
libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is to be removed.
  Package apache2-mpm-itk is not installed.
(Reading database ... 190156 files and directories currently installed.)
Removing apache2-mpm-prefork ...
[/B]* Stopping web server apache2
... waiting .   ...done.
Selecting previously unselected package apache2-mpm-itk.
(Reading database ... 190157 files and directories currently installed.)
Unpacking apache2-mpm-itk (from .../apache2-mpm-itk_2.2.22-1ubuntu1.4_amd64.deb) ...
Setting up apache2.2-bin (2.2.22-1ubuntu1.4) ...
Setting up apache2.2-common (2.2.22-1ubuntu1.4) ...
Setting up apache2-mpm-itk (2.2.22-1ubuntu1.4) ...
* Starting web server apache2
   ...done.
(Reading database ... 190156 files and directories currently installed.)
[B]Removing libapache2-mod-php5 ...
Module php5 disabled.[/B]
To activate the new configuration, you need to run:
  service apache2 restart
Setting up apache2 (2.2.22-1ubuntu1.4) ...
.. install complete.
===================

===================
xxxxxx@xxxxxx:~$ aptitude search apache2-mpm-
p   apache2-mpm-event               - Apache HTTP Server - event driven model
p   apache2-mpm-event:i386          - Apache HTTP Server - event driven model
p   apache2-mpm-itk                 - multiuser MPM for Apache 2.2
p   apache2-mpm-itk:i386            - multiuser MPM for Apache 2.2
i   apache2-mpm-prefork             - Apache HTTP Server - traditional non-threa
p   apache2-mpm-prefork:i386        - Apache HTTP Server - traditional non-threa
p   apache2-mpm-worker              - Apache HTTP Server - high speed threaded m
p   apache2-mpm-worker:i386         - Apache HTTP Server - high speed threaded m
===================

---

