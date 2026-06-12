---
title: "Errors when using Apt-get install"
date: 2012-07-09
forum: Installation &amp; Upgrades
---

### Post by sunblade16 on 2012-07-09
Hello,
I have had some issues lately when using sudo apt-get install :( Please Help

```
spotify@ben-Inspiron-531s:~$ zrun
The program 'zrun' is currently not installed.  You can install it by typing:
sudo apt-get install moreutils
spotify@ben-Inspiron-531s:~$ sudo apt-get install moreutils
[sudo] password for spotify: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libio-pty-perl libipc-run-perl
Suggested packages:
  libtime-duration-perl
The following NEW packages will be installed:
  libio-pty-perl libipc-run-perl moreutils
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 188 kB of archives.
After this operation, 705 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libio-pty-perl i386 1:1.08-1build2 [36.9 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main libipc-run-perl all 0.90-1 [100 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/universe moreutils i386 0.45 [50.4 kB]
Fetched 188 kB in 1s (158 kB/s)   
Selecting previously unselected package libio-pty-perl.
(Reading database ... 302277 files and directories currently installed.)
Unpacking libio-pty-perl (from .../libio-pty-perl_1%3a1.08-1build2_i386.deb) ...
Selecting previously unselected package libipc-run-perl.
Unpacking libipc-run-perl (from .../libipc-run-perl_0.90-1_all.deb) ...
Selecting previously unselected package moreutils.
Unpacking moreutils (from .../moreutils_0.45_i386.deb) ...
Processing triggers for man-db ...
Setting up qmail (1.06-4) ...

The hostname -f command returned: $1

Your system needs to have a fully qualified domain name (fqdn) in
order to install the var-qmail packages.

Installation aborted.

dpkg: error processing qmail (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of qmail-run:
 qmail-run depends on qmail (>= 1.06-2.1); however:
  Package qmail is not configured yet.
dpkg: error processing qmail-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up libio-pty-perl (1:1.08-1build2) ...
Setting up libipc-run-perl (0.90-1) ...
Setting up moreutils (0.45) ...
Errors were encountered while processing:
 qmail
 qmail-run
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by jmfal on 2012-07-09
This should help you set" fqdn" then you can try to install

[http://codeghar.wordpress.com/2008/05/10/fully-qualified-domain-name/](http://codeghar.wordpress.com/2008/05/10/fully-qualified-domain-name/)

---

