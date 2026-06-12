---
title: "CHIRP, Daily Update problem..."
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by David2009 on 2015-12-17
Hello.  I am having difficulties with the commands to get the daily updates for the CHIRP (amateur radio programming software).

To get the updates the instructions say to enter these lines, which I enter one at a time:
 
sudo apt-add-repository ppa:dansmith/chirp-snapshots
sudo apt-get update
sudo apt-get install chirp-daily

The first two run with no troubles.

Would someone be able to walk me through this, because I don't understand the output from the third command line:
 
david@david-Satellite-A305:~$ sudo apt-get install chirp-daily
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclass-factory-util-perl libclass-load-perl libclass-singleton-perl
  libdata-optlist-perl libdatetime-format-builder-perl
  libdatetime-format-iso8601-perl libdatetime-format-strptime-perl
  libdatetime-locale-perl libdatetime-perl libdatetime-timezone-perl
  libmodule-implementation-perl libmodule-runtime-perl libpackage-stash-perl
  libpackage-stash-xs-perl libparams-classify-perl libparams-util-perl
  libparams-validate-perl librpc-xml-perl libsub-install-perl libtry-tiny-perl
  libxml-parser-perl
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  chirp-daily
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
2 not fully installed or removed.
Need to get 0 B/343 kB of archives.
After this operation, 2,518 kB of additional disk space will be used.
(Reading database ... 199619 files and directories currently installed.)
Preparing to unpack .../chirp-daily_20151212~trusty~1_amd64.deb ...
Unpacking chirp-daily (20151212~trusty~1) ...
dpkg: error processing archive /var/cache/apt/archives/chirp-daily_20151212~trusty~1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/chirp/locale/pl/LC_MESSAGES/CHIRP.mo', which is also in package chirp 0.4.1-1.0~kamal~trusty
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/chirp-daily_20151212~trusty~1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@david-Satellite-A305:~$ 

Also, I saw that some package were no longer needed, so I tried to follow the instruction to remove the unnecessary files. Here is its output:
 
david@david-Satellite-A305:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
david@david-Satellite-A305:~$ 

Thank you.

David

---

### Post by SlidingHorn on 2015-12-17
Hi David...It sounds like you already have a version installed.  You can either remove it first and try again, or upgrade instead of installing.

Option A:

```
sudo apt-get remove chirp
```
(Then start over)

Option B:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
(This would assumedly pick up the most recent version of chirp from any repos)0

---

### Post by David2009 on 2015-12-17
Sliding Horn, thank you for your help.  I ran the first line, still was told I had unnecessary files, but don't know how to get rid of them (not much use having unneeded files on the drive), and the second line ran fine.  Agreeing with you, I suppose this will pick up the latest and greatest of CHIRP.

Any suggestions for me to get rid of unneeded programs:
 
The following packages were automatically installed and are no longer required:
  libclass-factory-util-perl libclass-load-perl libclass-singleton-perl
  libdata-optlist-perl libdatetime-format-builder-perl
  libdatetime-format-iso8601-perl libdatetime-format-strptime-perl
  libdatetime-locale-perl libdatetime-perl libdatetime-timezone-perl
  libmodule-implementation-perl libmodule-runtime-perl libpackage-stash-perl
  libpackage-stash-xs-perl libparams-classify-perl libparams-util-perl
  libparams-validate-perl librpc-xml-perl libsub-install-perl libtry-tiny-perl
  libxml-parser-perl python-suds python-support
Use 'apt-get autoremove' to remove them.

I ran this above command line, and this is the output:
 
david@david-Satellite-A305:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
david@david-Satellite-A305:~$

---

### Post by SlidingHorn on 2015-12-17
You need "sudo" to do the apt-get autoremove:

```
sudo apt-get autoremove
```

---

### Post by David2009 on 2015-12-17
Thank you, again.

---

