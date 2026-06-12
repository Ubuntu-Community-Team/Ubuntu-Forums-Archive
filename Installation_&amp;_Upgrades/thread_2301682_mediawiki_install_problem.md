---
title: "mediawiki install problem"
date: 2015-11-04
forum: Installation &amp; Upgrades
---

### Post by trato on 2015-11-04
I tried to install mediawiki with apt-get command, and I got this error:

root@sugar:~# apt-get install mediawiki
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libjs-jquery-form libjs-jquery-tipsy mediawiki-classes
  mediawiki-extensions-base
Suggested packages:
  mediawiki-extensions-math memcached clamav
Recommended packages:
  php-wikidiff2
The following NEW packages will be installed:
  libjs-jquery-form libjs-jquery-tipsy mediawiki mediawiki-classes
  mediawiki-extensions-base
0 upgraded, 5 newly installed, 0 to remove and 78 not upgraded.
Need to get 12.1 MB of archives.
After this operation, 71.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/](http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/) trusty/universe libjs-jquery-form all 8-2 [20.3 kB]
Get:2 [http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/](http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/) trusty/universe libjs-jquery-tipsy all 8-2 [8,608 B]
Get:3 [http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/](http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/) trusty/universe mediawiki-classes all 1:1.19.14+dfsg-1 [38.4 kB]
Get:4 [http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/](http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/) trusty/universe mediawiki all 1:1.19.14+dfsg-1 [11.6 MB]
Get:5 [http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/](http://sa-east-1.ec2.archive.ubuntu.com/ubuntu/) trusty/universe mediawiki-extensions-base all 3.6 [402 kB]
Fetched 12.1 MB in 1s (7,962 kB/s)
Preconfiguring packages ...
Selecting previously unselected package libjs-jquery-form.
(Reading database ... 65978 files and directories currently installed.)
Preparing to unpack .../libjs-jquery-form_8-2_all.deb ...
Unpacking libjs-jquery-form (8-2) ...
Selecting previously unselected package libjs-jquery-tipsy.
Preparing to unpack .../libjs-jquery-tipsy_8-2_all.deb ...
Unpacking libjs-jquery-tipsy (8-2) ...
Selecting previously unselected package mediawiki-classes.
Preparing to unpack .../mediawiki-classes_1%3a1.19.14+dfsg-1_all.deb ...
Unpacking mediawiki-classes (1:1.19.14+dfsg-1) ...
Selecting previously unselected package mediawiki.
Preparing to unpack .../mediawiki_1%3a1.19.14+dfsg-1_all.deb ...
Unpacking mediawiki (1:1.19.14+dfsg-1) ...
Selecting previously unselected package mediawiki-extensions-base.
Preparing to unpack .../mediawiki-extensions-base_3.6_all.deb ...
Unpacking mediawiki-extensions-base (3.6) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libjs-jquery-form (8-2) ...
Setting up libjs-jquery-tipsy (8-2) ...
Setting up mediawiki-classes (1:1.19.14+dfsg-1) ...
Setting up mediawiki (1:1.19.14+dfsg-1) ...
/var/lib/dpkg/info/mediawiki.postinst: 13: /var/lib/dpkg/info/mediawiki.postinst: php5enmod: not found
dpkg: error processing package mediawiki (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up mediawiki-extensions-base (3.6) ...
Errors were encountered while processing:
 mediawikiE: Sub-process /usr/bin/dpkg returned an error code (1)



I've tried to remove it and could not:


root@sugar:~# apt-get remove  mediawiki
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-jquery-form libjs-jquery-tipsy mediawiki-classes
  mediawiki-extensions-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mediawiki
0 upgraded, 0 newly installed, 1 to remove and 78 not upgraded.
1 not fully installed or removed.
After this operation, 68.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 68710 files and directories currently installed.)
Removing mediawiki (1:1.19.14+dfsg-1) ...
/var/lib/dpkg/info/mediawiki.prerm: 24: /var/lib/dpkg/info/mediawiki.prerm: php5dismod: not found
dpkg: error processing package mediawiki (--remove):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 mediawiki
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@sugar:~# apt-get purge mediawiki
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjs-jquery-form libjs-jquery-tipsy mediawiki-classes
  mediawiki-extensions-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mediawiki*
0 upgraded, 0 newly installed, 1 to remove and 78 not upgraded.
1 not fully installed or removed.
After this operation, 68.7 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 68710 files and directories currently installed.)
Removing mediawiki (1:1.19.14+dfsg-1) ...
/var/lib/dpkg/info/mediawiki.prerm: 24: /var/lib/dpkg/info/mediawiki.prerm: php5dismod: not found
dpkg: error processing package mediawiki (--purge):
 subprocess installed pre-removal script returned error exit status 127
Errors were encountered while processing:
 mediawiki
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@sugar:~# apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 78 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mediawiki (1:1.19.14+dfsg-1) ...
/var/lib/dpkg/info/mediawiki.postinst: 13: /var/lib/dpkg/info/mediawiki.postinst: php5enmod: not found
dpkg: error processing package mediawiki (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 mediawiki
E: Sub-process /usr/bin/dpkg returned an error code (1)


Did not found on google either here on forum.

---

