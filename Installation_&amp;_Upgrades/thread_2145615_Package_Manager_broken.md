---
title: "Package Manager broken"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by MarkySharky70 on 2013-05-16
After a recent update of my packages it appears to have failed while upgrading libssl1.0.0:i386 

I've tried all the common broken package manager stuff that I have been able to find and nothing has seemed to work.  I'm finally at my wits end and reaching out for help!  Here's where I am stuck at for the moment (note using Ubuntu 12.04 AMD64)

1. Downloaded then openssl package to my home directory directly from here: [http://www.ubuntuupdates.org/package/core/precise/main/updates/openssl](http://www.ubuntuupdates.org/package/core/precise/main/updates/openssl)

2. ```
sudo dpkg -i *.deb
(Reading database ... 485499 files and directories currently installed.)
Preparing to replace openssl 1.0.1-4ubuntu5.8 (using openssl_1.0.1-4ubuntu5.9_amd64.deb) ...
Unpacking replacement openssl ...
dpkg: dependency problems prevent configuration of openssl:
 openssl depends on libssl1.0.0 (>= 1.0.1); however:
  Package libssl1.0.0 is not configured yet.
dpkg: error processing openssl (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openssl
```

3. ```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  dvdrip-doc libgraphicsmagick3 libevent-perl libxine1-x libevent-rpc-perl subtitleripper libanyevent-perl libxine1-plugins
  libevent-execflow-perl ogmtools lsdvd libxine1-console fping libxine1-misc-plugins xine-ui dvdrip-utils libintl-perl
  libgtk2-ex-formfactory-perl libxine1-bin libxine1-ffmpeg libxine1 libapt-pkg4.12:i386 libsigc++-2.0-0c2a:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libapt-pkg4.12:i386 libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl
  libparse-debianchangelog-perl libsigc++-2.0-0c2a:i386 libssl1.0.0:i386 libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev libxml-simple-perl
The following packages will be REMOVED:
  aptitude:i386
The following NEW packages will be installed:
  aptitude libapt-pkg4.12:i386 libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl
  libparse-debianchangelog-perl libsigc++-2.0-0c2a:i386 libssl1.0.0:i386 libsub-name-perl
0 upgraded, 11 newly installed, 1 to remove and 57 not upgraded.
6 not fully installed or removed.
Need to get 0 B/5,007 kB of archives.
After this operation, 8,098 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
E: Internal Error, No file name for libssl1.0.0
```

4. ```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  dvdrip-doc libgraphicsmagick3 libevent-perl libxine1-x libevent-rpc-perl subtitleripper libanyevent-perl libxine1-plugins
  libevent-execflow-perl ogmtools lsdvd libxine1-console fping libxine1-misc-plugins xine-ui dvdrip-utils libintl-perl
  libgtk2-ex-formfactory-perl libxine1-bin libxine1-ffmpeg libxine1 libapt-pkg4.12:i386 libsigc++-2.0-0c2a:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude libapt-pkg4.12:i386 libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl
  libparse-debianchangelog-perl libsigc++-2.0-0c2a:i386 libssl1.0.0:i386 libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev libxml-simple-perl
The following packages will be REMOVED:
  aptitude:i386
The following NEW packages will be installed:
  aptitude libapt-pkg4.12:i386 libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl
  libparse-debianchangelog-perl libsigc++-2.0-0c2a:i386 libssl1.0.0:i386 libsub-name-perl
0 upgraded, 11 newly installed, 1 to remove and 57 not upgraded.
6 not fully installed or removed.
Need to get 0 B/5,007 kB of archives.
After this operation, 8,098 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
 E: Internal Error, No file name for libssl1.0.0
```

5. ```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 aptitude:i386 : Depends: libapt-pkg4.12:i386 (>= 0.8.16~exp12ubuntu6) but it is not installed
                 Depends: libboost-iostreams1.46.1:i386 (>= 1.46.1-1) but it is not installed
                 Depends: libcwidget3:i386 but it is not installed
                 Depends: libept1.4.12:i386 but it is not installed
                 Depends: libsigc++-2.0-0c2a:i386 (>= 2.0.2) but it is not installed
                 Depends: libxapian22:i386 but it is not installed
                 Recommends: sensible-utils:i386 but it is not installable
                 Recommends: apt-xapian-index:i386 but it is not installable
                 Recommends: libparse-debianchangelog-perl:i386 but it is not installable
 ia32-libs-multiarch:i386 : Depends: libssl1.0.0:i386 but it is not installed
 libcurl3:i386 : Depends: libssl1.0.0:i386 (>= 1.0.1) but it is not installed
 libsasl2-modules:i386 : Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not installed
 ppa-purge : Depends: aptitude but it is not installed
 skype:i386 : Depends: libssl1.0.0:i386 but it is not installed
              Recommends: sni-qt:i386 but it is not installed
E: Unmet dependencies. Try using -f.
```

6. ```
$ sudo apt-get clean
$ sudo apt-get autoremove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl
  libparse-debianchangelog-perl libssl1.0.0:i386 libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev libxml-simple-perl
The following packages will be REMOVED:
  aptitude:i386 dvdrip-doc dvdrip-utils fping libanyevent-perl libevent-execflow-perl libevent-perl libevent-rpc-perl
  libgraphicsmagick3 libgtk2-ex-formfactory-perl libintl-perl libxine1 libxine1-bin libxine1-console libxine1-ffmpeg
  libxine1-misc-plugins libxine1-plugins libxine1-x lsdvd ogmtools subtitleripper xine-ui
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3 libept1.4.12 libio-string-perl
  libparse-debianchangelog-perl libssl1.0.0:i386 libsub-name-perl
0 upgraded, 9 newly installed, 22 to remove and 57 not upgraded.
6 not fully installed or removed.
Need to get 4,054 kB of archives.
After this operation, 17.3 MB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libboost-iostreams1.46.1 amd64 1.46.1-7ubuntu3 [39.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libcwidget3 amd64 0.5.16-3.1ubuntu1 [406 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main libept1.4.12 amd64 1.0.6~exp1ubuntu1 [129 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main aptitude amd64 0.6.6-1ubuntu1.2 [2,372 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libssl1.0.0 i386 1.0.1-4ubuntu5.9 [1,005 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise/main libsub-name-perl amd64 0.05-1build2 [9,656 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/main libio-string-perl all 1.08-2 [12.0 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Fetched 4,054 kB in 3s (1,108 kB/s)                      
E: Internal Error, No file name for libssl1.0.0
```

7. ```
sudo dpkg --purge --force-depends libssl1.0.0:i386
dpkg: libssl1.0.0:i386: dependency problems, but removing anyway as you requested:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0).
 libcurl3:i386 depends on libssl1.0.0 (>= 1.0.1).
 ia32-libs-multiarch:i386 depends on libssl1.0.0.
 skype:i386 depends on libssl1.0.0.
(Reading database ... 485498 files and directories currently installed.)
Removing libssl1.0.0:i386 ...
Purging configuration files for libssl1.0.0:i386 ...
Out of memory!
dpkg: error processing libssl1.0.0:i386 (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libssl1.0.0:i386

```

8. ```
sudo dpkg --configure -a
Setting up libssl1.0.0 (1.0.1-4ubuntu5.9) ...
Setting up man-db (2.6.1-2ubuntu1) ...
Out of memory!
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openssl (1.0.1-4ubuntu5.9) ...
dpkg: dependency problems prevent configuration of ppa-purge:
 ppa-purge depends on aptitude; however:
  Package aptitude is not installed.
dpkg: error processing ppa-purge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptitude:i386:
 aptitude:i386 depends on libapt-pkg4.12 (>= 0.8.16~exp12ubuntu6).
 aptitude:i386 depends on libboost-iostreams1.46.1 (>= 1.46.1-1).
 aptitude:i386 depends on libcwidget3.
 aptitude:i386 depends on libept1.4.12.
 aptitude:i386 depends on libsigc++-2.0-0c2a (>= 2.0.2).
 aptitude:i386 depends on libxapian22.
dpkg: error processing aptitude:i386 (--configure):
 dependency problems - leaving unconfigured
Setting up libssl-dev (1.0.1-4ubuntu5.9) ...
Errors were encountered while processing:
 man-db
 ppa-purge
 aptitude:i386

```

...at this point most any apt-get command ends up failing over this libssl1.0.0 problem and I'm at a total loss.  Any help is most appreciated.

---

