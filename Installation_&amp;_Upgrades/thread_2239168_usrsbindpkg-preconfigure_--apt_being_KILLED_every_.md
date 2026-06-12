---
title: "/usr/sbin/dpkg-preconfigure --apt being KILLED every time?"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by MickoD on 2014-08-12
Hi all,

I'm a little perplexed with an issue I'm seeing on one of my linux boxes. Seems I wasn't paying enough attention doing an apt-get install and in trying to correct it with an apt-get autoremove, a huge amount of packages were removed from my system :(

If I do an apt-get -f install I get the following;

```
-bash-4.2#  apt-get -f install    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ramlog rsync
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  rsync
Suggested packages:
  openssh-client openssh-server
The following packages will be REMOVED:
  unzip vsftpd
The following NEW packages will be installed:
  rsync
0 upgraded, 1 newly installed, 2 to remove and 164 not upgraded.
3 not fully installed or removed.
Need to get 0 B/353 kB of archives.
After this operation, 157 kB disk space will be freed.
Do you want to continue [Y/n]? 
/bin/sh: line 1:  7293 Killed                  /usr/sbin/dpkg-preconfigure --apt
dpkg: warning: files list file for package 'libssh2-1:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwrap0:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapr1:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpng12-0:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevent-2.0-5:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libldap-2.4-2:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblua5.1-0:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcre3:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdb5.3:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnfsidmap2:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjpeg8:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-2:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsasl2-modules:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1-ldap:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdevmapper1.02.1:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexpat1:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libltdl7:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaprutil1-dbd-sqlite3:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmagic1:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libparted0debian1:armhf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxml2:armhf' missing; assuming package has no files currently installed
(Reading database ... 12550 files and directories currently installed.)
Removing unzip ...
/var/lib/dpkg/info/unzip.postrm: line 5:  7297 Killed                  update-mime
dpkg: error processing unzip (--remove):
 subprocess installed post-removal script returned error exit status 137
Removing vsftpd ...
/var/lib/dpkg/info/vsftpd.postrm: line 5:  7299 Killed                  deluser --quiet --system ${_USERNAME}
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 137
Errors were encountered while processing:
 unzip
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

In fact if I do an apt-get -f upgrade or just an apt-get upgrade, the process fails every time following this line initally;

```
/bin/sh: line 1:  7293 Killed                  /usr/sbin/dpkg-preconfigure --apt
```

I need to try and reinstall all the packages that were previously installed (which I believe I have in a console log on the actual machine in question) and I'm really not sure why apt-get is playing up on me.

Any assistance would be hugely appreciate here!

Thanks in advance,

Mick

---

