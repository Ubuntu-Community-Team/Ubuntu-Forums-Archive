---
title: "Can't sudo-apt anything - fatal error? sounds bad"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by pryan75 on 2010-03-05
Hi there,

Receive the following error when trying to sudo apt-get autoremove or upgrade

```
patrick@pryan75:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  ca-certificates-java icedtea-6-jre-cacao java-common java-wrappers libaccess-bridge-java libaccess-bridge-java-jni libcommons-cli-java libcommons-lang-java
  libjline-java liblog4j1.2-java libswt-cairo-gtk-3.4-jni libswt-gnome-gtk-3.4-jni libswt-gtk-3.4-java libswt-gtk-3.4-jni libswt-mozilla-gtk-3.4-jni
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib rhino tzdata-java
0 upgraded, 0 newly installed, 20 to remove and 93 not upgraded.
1 not fully installed or removed.
After this operation, 95.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 5%dpkg: [B]unrecoverable fatal error, aborting:
 files list file for package `desktop-file-utils' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)[/B]
patrick@pryan75:~$

```

Contents of file in question are as:

```
/etc/bash_completion.d/desktop-file-validate
/etc/gnome/defaults.list
/usr/bin/desktop-file-install
/usr/bin/desktop-file-validate
/usr/bin/update-desktop-database
/usr/share/applications/defaults.list
/usr/share/doc/desktop-file-utils/AUTHORS
/usr/share/doc/desktop-file-utils/NEWS.gz
/usr/share/doc/desktop-file-utils/README
/usr/share/doc/desktop-file-utils/TODO.Debian
/usr/share/doc/desktop-file-utils/changelog.Debian.gz
/usr/share/doc/desktop-file-utils/copyright
/usr/share/man/man1/desktop-file-validate.1.gz
/usr/share/man/man8/desktop-file-install.8.gz
```

Maybe this error log has something?:

```
ProblemType: Package
Architecture: i386
Date: Fri Mar  5 21:08:08 2010
Package: doc-base 0.9.3
SourcePackage: doc-base
ErrorMessage:
 subprocess installed post-installation script returned error exit status 2
DpkgTerminalLog:
 
 Log started: 2010-03-04  15:16:25
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-04  15:16:25
 
 Log started: 2010-03-04  15:16:48
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-04  15:16:48
 
 Log started: 2010-03-05  20:38:46
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-05  20:38:47
 
 Log started: 2010-03-05  20:40:24
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-05  20:40:25
 
 Log started: 2010-03-05  20:42:44
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-05  20:42:44
 
 Log started: 2010-03-05  20:44:40
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-05  20:44:40
 
 Log started: 2010-03-05  20:46:29
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-05  20:46:29
 
 Log started: 2010-03-05  20:50:58
 (Reading database ... 
(Reading database ... 5%dpkg: unrecoverable fatal error, aborting:

  files list file for package 'desktop-file-utils' is missing final newline

 Log ended: 2010-03-05  20:50:59
 
 Log started: 2010-03-05  20:54:35
 Log ended: 2010-03-05  20:54:35
 
 Log started: 2010-03-05  21:08:08
 Setting up doc-base (0.9.3) ...

 MLDBM error: Second level tie failed, "No such file or directory" at /usr/share/perl5/Debian/DocBase/DB.pm line 44

 Can't access /var/lib/doc-base/info/files.db: No such file or directory

  at /usr/share/perl5/Debian/DocBase/DocBaseFile.pm line 64

 dpkg: error processing doc-base (--configure):

  subprocess installed post-installation script returned error exit status 2

AptOrdering:
 doc-base: Configure
Dmesg:
 <removed extraneous logging>
Dependencies:
 base-files 5.0.0ubuntu7
 base-passwd 3.5.21
 coreutils 7.4-2ubuntu1
 debconf 1.5.27ubuntu2
 debconf-i18n 1.5.27ubuntu2
 debianutils 2.30ubuntu3
 dpkg 1.15.4ubuntu2
 findutils 4.4.2-1
 gcc-4.4-base 4.4.1-4ubuntu9
 libacl1 2.2.47-2
 libattr1 1:2.4.43-3
 libc-bin 2.10.1-0ubuntu16
 libc6 2.10.1-0ubuntu16
 libdb4.7 4.7.25-7ubuntu2
 libgcc1 1:4.4.1-4ubuntu9
 libgdbm3 1.8.3-4
 liblocale-gettext-perl 1.05-4build1
 libmldbm-perl 2.01-2
 libpam-modules 1.1.0-2ubuntu1
 libpam-runtime 1.1.0-2ubuntu1
 libpam0g 1.1.0-2ubuntu1
 libselinux1 2.0.85-2ubuntu2
 libstdc++6 4.4.1-4ubuntu9
 libtext-charwidth-perl 0.04-5build1
 libtext-iconv-perl 1.7-1build1
 libtext-wrapi18n-perl 0.06-7
 libuuid-perl 0.02-3build1
 libuuid1 2.16-1ubuntu5
 lzma 4.43-14ubuntu1
 passwd 1:4.1.4.1-1ubuntu2
 perl 5.10.0-24ubuntu4
 perl-base 5.10.0-24ubuntu4
 perl-modules 5.10.0-24ubuntu4
 tzdata 2009u-0ubuntu0.9.10
 zlib1g 1:1.2.3.3.dfsg-13ubuntu3
DistroRelease: Ubuntu 9.10
PackageArchitecture: all
ProcVersionSignature: Ubuntu 2.6.31-17.54-generic
Title: package doc-base 0.9.3 failed to install/upgrade: subprocess installed post-installation script returned error exit status 2
Uname: Linux 2.6.31-17-generic i686
```

If anyone has any ideas, I'm wide open here.

I have tried: reinstalling doc-base & desktop-file-utils, get the same error. I edited the desktop-file-utils to what is listed on Ubuntu main site. I tried forcing it with ```
sudo dpkg -r --force-all desktop-file-utils
``` same error.

Any guidance is much appreciated.

Pr

---

### Post by bcbc on 2010-03-06
Here's an old bug posted on this. It sounds like you could delete the file in question (under /var/lib/dpkg/info/...) 

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189)

---

### Post by pryan75 on 2010-03-06
sweet,

this worked:

first, edit /var/lib/dpkg/info/desktop-file-utils.list so that there are no extra lines at the bottom of the file. I had manually edited this file to remove a line of garbage...as outlined in the forum post provided by bcbc [thanks sir]

then:

```
sudo dpkg -r --force-all doc-base
```

then:

```
sudo dpkg -i --force-all doc-base

```

and while I am not sure why this worked, I'm thankful it did.

Pr

---

