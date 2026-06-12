---
title: "php-pear fails to install"
date: 2015-06-03
forum: Installation &amp; Upgrades
---

### Post by whaase on 2015-06-03
I've been trying to update my server for several months and I keep running into this issue with php-pear (part of Owncloud install). Every time I try i get this error and I have to restore from a backup as this seems to toast it. Can anyone point me to something I may be missing?

```
sudo apt-get install php-pear
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  php5-dev
The following packages will be upgraded:
  php-pear
1 upgraded, 0 newly installed, 0 to remove and 87 not upgraded.
Need to get 267 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main php-pear all 5.5.9+dfsg-1ubuntu4.9 [267 kB]
Fetched 267 kB in 0s (289 kB/s)   
(Reading database ... 95719 files and directories currently installed.)
Preparing to unpack .../php-pear_5.5.9+dfsg-1ubuntu4.9_all.deb ...
Unpacking php-pear (5.5.9+dfsg-1ubuntu4.9) over (5.5.9+dfsg-1ubuntu4.7) ...
dpkg: error processing archive /var/cache/apt/archives/php-pear_5.5.9+dfsg-1ubuntu4.9_all.deb (--unpack):
 unable to stat `./usr/share/doc/php5-common/PEAR/XML_Util/examples/example.php.gz' (which I was about to install): Input/output error
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/share/lintian/overrides/php-pear': Read-only file system
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/bin/pear': Read-only file system
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/bin/pecl': Read-only file system
dpkg: error while cleaning up:
 unable to restore backup version of `/usr/bin/peardev': Read-only file system
dpkg: error while cleaning up:
 unable to securely remove '/var/lib/dpkg/tmp.ci': Read-only file system
dpkg: error while cleaning up:
 unable to securely remove '/var/lib/dpkg/reassemble.deb': Read-only file system
dpkg: error: unable to create new file '/var/lib/dpkg/available-new': Read-only file system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)touch: cannot touch ‘/var/lib/update-notifier/dpkg-run-stamp’: Read-only file system
sh: 1: cannot create /var/lib/update-notifier/updates-available: Read-only file system
E: Sub-process /usr/bin/dpkg returned an error code (2)
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier ]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi '
E: Sub-process returned an error code

```

Thanks, Walter

---

