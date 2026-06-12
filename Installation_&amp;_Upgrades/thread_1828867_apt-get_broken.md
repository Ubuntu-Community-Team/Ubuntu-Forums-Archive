---
title: "apt-get broken"
date: 2011-08-19
forum: Installation &amp; Upgrades
---

### Post by mfpockets on 2011-08-19
Hello, 

I recently upgraded my vps from 8.04 to 11.04.  

When I run apt-get upgrade I get 

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libgtk2.0-0 : Depends: libcups2 (>= 1.4.0) but it is not installed
E: Unmet dependencies. Try using -f.

```

If I try apt-get install -f I get

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  x11-apps libfreebob0 libstdc++5 libio-compress-zlib-perl libiec61883-0 libcompress-zlib-perl xbase-clients libstdc++5-3.3-dev g++-3.3 x11-xfs-utils
  python-numeric libio-compress-base-perl xutils apparmor-profiles libboost-thread1.34.1 libboost-date-time1.34.1 libpango1.0-common libdirectfb-1.0-0
  libffi4 libltdl3-dev libgsf-1-common python-pyopenssl python-dbus xinit x11-session-utils libfs6 libboost-filesystem1.34.1 libgsf-1-114 xutils-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcups2
Suggested packages:
  cups-common
The following NEW packages will be installed:
  libcups2
0 upgraded, 1 newly installed, 0 to remove and 222 not upgraded.
170 not fully installed or removed.
Need to get 0 B/158 kB of archives.
After this operation, 479 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 42492 files and directories currently installed.)
Unpacking libcups2 (from .../libcups2_1.4.6-5ubuntu1.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcups2_1.4.6-5ubuntu1.3_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libcups.so.2', which is also in package libcupsys2 1.3.7-1ubuntu3.12
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libcups2_1.4.6-5ubuntu1.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas on how to resolve this?

---

### Post by riverfr0zen on 2011-08-19
Try out the fix suggested here:
[http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)

---

