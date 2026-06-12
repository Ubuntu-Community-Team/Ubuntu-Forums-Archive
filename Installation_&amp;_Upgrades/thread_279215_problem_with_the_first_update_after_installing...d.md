---
title: "problem with the first update after installing...dependencies"
date: 2006-10-17
forum: Installation &amp; Upgrades
---

### Post by Cal1066 on 2006-10-17
Ok I have tried several things to fix this...here is the message...followed by some ineffective trys to fix the problem!
bubba99n@cb-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libglib2.0-data: Depends: libglib2.0-0 (= 2.10.3-0ubuntu1) but 2.10.2-1ubuntu3 is installed
  libgnomeui-0: Depends: libgnomeui-common (= 2.14.1-0ubuntu2) but 2.14.1-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
bubba99n@cb-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libpango1.0-0
  libpango1.0-common
Suggested packages:
  ttf-thryomanes
Recommended packages:
  libgnomevfs2-extra
The following packages will be upgraded:
  libglib2.0-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libpango1.0-0
  libpango1.0-common
6 upgraded, 0 newly installed, 0 to remove and 174 not upgraded.
31 not fully installed or removed.
Need to get 0B/6319kB of archives.
After unpacking 8192B disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Can't exec "/tmp/libpango1.0-common.config.145971": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /tmp/libpango1.0-common.config.145971 configure 1.12.2-0ubuntu3 failed at /usr/share/perl5/Debconf/ConfModule.pm line 57
libpango1.0-common failed to preconfigure, with exit status 2
(Reading database ... 69758 files and directories currently installed.)
Preparing to replace gzip 1.3.5-12 (using .../gzip_1.3.5-12_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Permission denied
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Permission denieddpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bubba99n@cb-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libglib2.0-data: Depends: libglib2.0-0 (= 2.10.3-0ubuntu1) but 2.10.2-1ubuntu3 is installed
  libgnomeui-0: Depends: libgnomeui-common (= 2.14.1-0ubuntu2) but 2.14.1-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
bubba99n@cb-desktop:~$ sudo apt-get install libglib2.0-0
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgnomeui-0: Depends: libgnomeui-common (= 2.14.1-0ubuntu2) but 2.14.1-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bubba99n@cb-desktop:~$ sudo apt-get install libgnomeui-common
Reading package lists... Done
Building dependency tree... Done
libgnomeui-common is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libglib2.0-data: Depends: libglib2.0-0 (= 2.10.3-0ubuntu1) but 2.10.2-1ubuntu3 is to be installed
  libgnomeui-0: Depends: libgnomeui-common (= 2.14.1-0ubuntu2) but 2.14.1-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bubba99n@cb-desktop:~$ sudo apt-get -f install libglib2.0-0 libgnomeui-common
Reading package lists... Done
Building dependency tree... Done
libgnomeui-common is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libgnomeui-0: Depends: libgnomeui-common (= 2.14.1-0ubuntu2) but 2.14.1-0ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bubba99n@cb-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libglib2.0-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libpango1.0-0
  libpango1.0-common
Suggested packages:
  ttf-thryomanes
Recommended packages:
  libgnomevfs2-extra
The following packages will be upgraded:
  libglib2.0-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libpango1.0-0
  libpango1.0-common
6 upgraded, 0 newly installed, 0 to remove and 174 not upgraded.
31 not fully installed or removed.
Need to get 0B/6319kB of archives.
After unpacking 8192B disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Can't exec "/tmp/libpango1.0-common.config.147891": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm line 168.
open2: exec of /tmp/libpango1.0-common.config.147891 configure 1.12.2-0ubuntu3 failed at /usr/share/perl5/Debconf/ConfModule.pm line 57
libpango1.0-common failed to preconfigure, with exit status 2
(Reading database ... 69758 files and directories currently installed.)
Preparing to replace gzip 1.3.5-12 (using .../gzip_1.3.5-12_i386.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Permission denied
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg (subprocess): unable to execute new pre-removal script: Permission denied
dpkg: error processing /var/cache/apt/archives/gzip_1.3.5-12_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Permission denieddpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/gzip_1.3.5-12_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bubba99n@cb-desktop:~$

---

