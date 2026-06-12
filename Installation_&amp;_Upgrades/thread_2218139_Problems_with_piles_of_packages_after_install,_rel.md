---
title: "Problems with piles of packages after install, related to libperl.so.5.14"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by 5-daqid-9 on 2014-04-19
Couple of days into my upgrade experience, I have fixed most problems, but have a bunch of problems with a lot of packages apparently because they are all wanting an obsolete version of perl (or at least that is my interpretation).

Example apt-get install output:

```
Processing triggers for man-db (2.6.7.1-1) ...perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
Setting up libpaper1:amd64 (1.1.24+nmu2ubuntu3) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package libpaper1:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of cups-daemon:
 cups-daemon depends on libpaper1; however:
  Package libpaper1:amd64 is not configured yet.


dpkg: error processing package cups-daemon (--configure):
 dependency problems - leaving unconfigured
Setting up php5-common (5.5.9+dfsg-1ubuntu4) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package php5-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of php5-cli:
 php5-cli depends on php5-common (= 5.5.9+dfsg-1ubuntu4); however:
  Package php5-common is not configured yet.


dpkg: error processing package php5-cli (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of php5-readline:
 php5-readline depends on phpapi-20121212; however:
  Package phpapi-20121212 is not installed.
  Package php5-common which provides phpapi-20121212 is not configured yet.
 php5-readline depends on php5-common (= 5.5.9+dfsg-1ubuntu4); however:
  Package php5-common is not configured yet.
 php5-readline depends on php5-cli (= 5.5.9+dfsg-1ubuntu4); however:
  Package php5-cli is not configured yet.


dpkg: error processing package php5-readline (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Setting up samba-common (2:4.1.6+dfsg-1ubuntu2) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package samba-common (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up rsyslog (7.4.4-1ubuntu2) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up ufw (0.34~rc-0ubuntu2) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package ufw (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up dwww (1.12.1) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
system ucf --debconf-ok --three-way /etc/dwww/dwww.conf.dpkg-new /etc/dwww/dwww.conf failed: Inappropriate ioctl for device
dpkg: error processing package dwww (--configure):
 subprocess installed post-installation script returned error exit status 25
No apport report written because MaxReports has already been reached
                                                                    Setting up gconf2-common (3.2.6-0ubuntu2) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package gconf2-common (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up hplip (3.14.3-0ubuntu3) ...
Creating/updating hplip user account...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package hplip (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up nfs-common (1:1.2.8-6ubuntu1) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up openssh-server (1:6.6p1-2ubuntu1) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up tomcat7 (7.0.52-1) ...
perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package tomcat7 (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up grub-efi-amd64 (2.02~beta2-9) ...
No apport report written because MaxReports has already been reached
                                                                    perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
dpkg: error processing package grub-efi-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports has already been reached
                                                                    Setting up libb-keywords-perl (1.13-1) ...
Setting up libclass-data-inheritable-perl (0.08-2) ...
Setting up libclass-method-modifiers-perl (2.09-1) ...
Setting up libclass-tiny-perl (0.012-1) ...
Setting up libconfig-tiny-perl (2.20-1) ...
Setting up libdevel-stacktrace-perl (1.3000-1) ...
Setting up libemail-address-perl (1.900-1) ...
Setting up libexception-class-perl (1.37-1) ...
Setting up libfile-find-rule-perl-perl (1.13-1) ...
Setting up libparams-classify-perl (0.013-4build2) ...
Setting up libmodule-runtime-perl (0.013-1) ...
Setting up libpath-tiny-perl (0.052-1) ...
Setting up librole-tiny-perl (1.003002-1) ...
Setting up libpath-isdev-perl (1.000002-1) ...
Setting up libpath-finddev-perl (0.4.0-1) ...
Setting up libfile-sharedir-projectdistdir-perl (0.5.2-1) ...
Setting up liblingua-en-inflect-perl (1.895-1) ...
Setting up libpod-spell-perl (1.12-1) ...
Setting up libreadonly-perl (1.04-1) ...
Setting up libppix-utilities-perl (1.001000-1) ...
Setting up libreadonly-xs-perl (1.05-1) ...
Setting up libstring-format-perl (1.17-1) ...
Setting up perltidy (20120701-1) ...
Setting up libperl-critic-perl (1.121-1) ...
Setting up libperl-minimumversion-perl (1.32-1) ...
Setting up libunicode-utf8-perl (0.59-1build1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 libpaper1:amd64
 cups-daemon
 php5-common
 php5-cli
 php5-readline
 samba-common
 rsyslog
 ufw
 dwww
 gconf2-common
 hplip
 nfs-common
 openssh-server
 tomcat7
 grub-efi-amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

This may or may not be helpful, in that it shows that I have two perl lib folders...

```
{{my name}}@{{my computer's name}} /v/l/dpkg> cd /usr/local/lib/perl/{{my name}}@{{my computer's name}} /u/l/l/perl> ls
5.14.2/  5.18.2/
{{my name}}@{{my computer's name}} /u/l/l/perl> cd 5.14.2/
{{my name}}@{{my computer's name}} /u/l/l/p/5.14.2> ls
Attribute/  DateTime/    DateTimePPExtra.pm  List/     Params/
auto/       DateTime.pm  DateTimePP.pm       Package/  perllocal.pod
{{my name}}@{{my computer's name}} /u/l/l/p/5.14.2> cd ..
{{my name}}@{{my computer's name}} /u/l/l/perl> ls
5.14.2/  5.18.2/
{{my name}}@{{my computer's name}} /u/l/l/perl> cd 5.18.2
{{my name}}@{{my computer's name}} /u/l/l/p/5.18.2> ls
auto/      dbixs_rev.pl  Filter/  Net/           threads/     Win32/
Bundle/    Devel/        IO/      Parse/         threads.pm   Wx/
Compress/  Digest/       IPC/     perllocal.pod  Time/        Wx.pm
Data/      Encode/       JSON/    Scalar/        Unicode/
DBD/       Encode.pm     List/    Socket.pm      version/
DBI/       encoding.pm   Math/    Storable.pm    version.pm
DBI.pm     FCGI.pm       MIME/    Sys/           version.pod



```

Additionally, so might this:

```
{{my name}}@{{my computer's name}} /u/l/lib [124]> which perl
/usr/local/bin/perl
{{my name}}@{{my computer's name}} /u/l/lib> whereis perl
perl: /usr/bin/perl /etc/perl /usr/lib/perl /usr/bin/X11/perl /usr/local/bin/perl /usr/local/lib/perl /usr/share/perl /usr/share/man/man1/perl.1.gz
{{my name}}@{{my computer's name}} /u/l/lib> /usr/local/bin/perl -e "print 'derp'"
/usr/local/bin/perl: error while loading shared libraries: libperl.so.5.14: cannot open shared object file: No such file or directory
{{my name}}@{{my computer's name}} /u/l/lib [127]> /usr/bin/perl -e "print 'derp'"
derp&#9166;                                                                           



```

So I must have two perls going on and/or a perl config problem...

---

### Post by 5-daqid-9 on 2014-04-20
No ideas anyone? I'm inclined to simlink the old perl to the new one, any thoughts on this? I don't really know what I am doing as is probably quite apparent...

---

### Post by bapoumba on 2014-04-20
Well, I have not read in details but it is quite strange that you need an older version of a package in main.
```
apt-cache policy perl
perl:
  Installed: 5.18.2-2ubuntu1
  Candidate: 5.18.2-2ubuntu1
  Version table:
 *** 5.18.2-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status

locate libperl.so.
/usr/lib/libperl.so.5.18
/usr/lib/libperl.so.5.18.2


```
I would rather suspect some repo in your sources.list or some ppa that may not have been updated to Trusty.

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by 5-daqid-9 on 2014-04-21
Thanks for trying anyway - but removing the old perl and putting new perl binary there (rather than symlinking) fixed the issue. I think in hindsight I have a vague recollection of putting the old perl binary there in the first place because I had to make some changes to an old website that expected it to be there (i.e. /usr/local/bin/) and it was quicker to do that than go through all the scripts changing them (and remembering to change it back when it went live!)

Not sure if this will actually help anyone, but there's probably another fool like me somewhere that will benefit from this thread :D

---

### Post by bapoumba on 2014-04-21
Ah la la, the old quick and dirty stuff that remains behind and gets forgotten :)
Thanks for marking your thread as solved!

---

