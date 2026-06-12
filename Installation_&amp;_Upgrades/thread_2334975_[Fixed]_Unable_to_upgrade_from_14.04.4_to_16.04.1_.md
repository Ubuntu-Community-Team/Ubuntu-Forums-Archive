---
title: "[Fixed] Unable to upgrade from 14.04.4 to 16.04.1 : sysv is broken"
date: 2016-08-24
forum: Installation &amp; Upgrades
---

### Post by Shadow aok on 2016-08-24
Hello,

I'm trying to upgrade an Ubuntu 14.04.4 AMD64 server, running inside a lxc container, running mainly request-tracker, apache2, bind and mysql.

do-release-upgrade fails every time (i can restore a backup to try again) :
```
Setting up sysv-rc (2.88dsf-59.3ubuntu2) ...
info: Reordering boot system, log to /var/lib/insserv/run-20160824T1014.log
error: Something failed while migrating.
 error: Unable to migrate to dependency based boot sequencing.
 See [http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot](http://wiki.debian.org/LSBInitScripts/DependencyBasedBoot) for
more information about dependency based boot sequencing. To
reattempt the migration process run 'dpkg --configure sysv-rc'.
 dpkg: error processing package sysv-rc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sysv-rc
Error in function:
 A fatal error occurred
 Please report this as a bug and include the files
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in
your report. The upgrade has aborted.
Your original sources.list was saved in
/etc/apt/sources.list.distUpgrade.
 SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
 Could not install the upgrades
 The upgrade has aborted. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).
 Please report this bug in a browser at
[http://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+filebug](http://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+filebug)
and attach the files in /var/log/dist-upgrade/ to the bug report.
installArchives() failed
```


 * /var/lib/insserv/run-20160824T1014.log
```
info: Converting rc0.d/S* and rc6.d/S* to K*.
info: running insserv
insserv: warning: script 'bind9' missing LSB tags and overrides
insserv: warning: script 'wide-dhcpv6-client' missing LSB tags and overrides
insserv: There is a loop between service bind9 and apache2 if stopped
insserv:  loop involving service apache2 at depth 2
insserv:  loop involving service bind9 at depth 1
insserv:  loop involving service sendsigs at depth 4
insserv: exiting now without changing boot order!
```

 So, i removed bind9 and apache2 from init.d and tried to fix it :
```
 ~# dpkg --configure sysv-rc
dpkg: error processing package sysv-rc (--configure):
 package sysv-rc is already installed and configured
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for ca-certificates (20160104ubuntu0.14.04.1) ...
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....done.
Errors were encountered while processing:
 sysv-rc
```

I'm missing some important binairies (like halt, shutdown and runlevel) :
```
/usr/sbin/invoke-rc.d: 1: /usr/sbin/invoke-rc.d: /sbin/runlevel: not found
```

```
~# apt-get install systemd-sysv
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc-dev-bin : Depends: libc6 (< 2.20) but 2.23-0ubuntu3 is to be installed
                Recommends: manpages-dev but it is not going to be installed
 libc6-dev : Depends: libc6 (= 2.19-0ubuntu6.9) but 2.23-0ubuntu3 is to be installed
 systemd-sysv : PreDepends: systemd
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 ~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libapache-dbi-perl libtest-requires-perl libtime-modules-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc-dev-bin libc6-dev manpages
Suggested packages:
  glibc-doc man-browser
Recommended packages:
  manpages-dev
The following NEW packages will be installed:
  manpages
The following packages will be upgraded:
  libc-dev-bin libc6-dev
2 upgraded, 1 newly installed, 0 to remove and 369 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3 240 kB of archives.
After this operation, 2 457 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Unescaped left brace in regex is deprecated, passed through in regex;  marked by <-- HERE in m/^(.*?)(\\)?\${ <-- HERE ([^{}]+)}(.*)$/ at  /usr/share/perl5/Debconf/Question.pm line 72.
Unescaped left brace in regex is deprecated, passed through in regex;  marked by <-- HERE in m/\${ <-- HERE ([^}]+)}/ at /usr/share/perl5/Debconf/Config.pm line 30.
Selecting previously unselected package manpages.
(Reading database ... 33169 files and directories currently installed.)
Preparing to unpack .../manpages_4.04-2_all.deb ...
Unpacking manpages (4.04-2) ...
Replacing files in old package libc-dev-bin (2.19-0ubuntu6.9) ...
Preparing to unpack .../libc6-dev_2.23-0ubuntu3_amd64.deb ...
Unpacking libc6-dev:amd64 (2.23-0ubuntu3) over (2.19-0ubuntu6.9) ...
Preparing to unpack .../libc-dev-bin_2.23-0ubuntu3_amd64.deb ...
Unpacking libc-dev-bin (2.23-0ubuntu3) over (2.19-0ubuntu6.9) ...
Setting up plymouth (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service udev has to be enabled to start service plymouth
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package plymouth (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on plymouth; however:
  Package plymouth is not configured yet.
 dpkg: error processing package mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on mountall; however:
  Package mountall is not configured yet.
 dpkg: error processing package upstart (--configure):
 dependency problems - leaving unconfigured
Setting up manpages (4.04-2) ...
Setting up libc-dev-bin (2.23-0ubuntu3) ...
Setting up libc6-dev:amd64 (2.23-0ubuntu3) ...
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
Errors were encountered while processing:
 plymouth
 mountall
 upstart
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I created a bug here, but since i only have this issue with one container (although they all use the same template), i don't know if it's gonna stay open :
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1616368](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1616368)

Any idea ?

Thanks.

---

### Post by Shadow aok on 2017-01-12
Ok, as i had this issue again, i fixed it by removing postfix before doing the upgrade (apt-get remove postfix).

---

### Post by Bucky Ball on 2017-01-12
Good news. To mark this thread correctly as solved, please see the last blue link in my signature at the bottom of this post.

Enjoy! ;)

---

### Post by Shadow aok on 2017-01-12
Done :)

---

