---
title: "Need Help installing FTP server (pure ftpd or proftpd)"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by briancastellanos on 2008-02-01
Hi, I am having trouble t yring to reinstall proftpd. 

I had used apt-get to install proftpd but somehow ended up compiling a version on top of it. It removed the apt-get version, then the compiled version was removed by rm -rf each of the files directories.

I try to reinstall proftpd but now it says that the version is up to date even though there is nothing installed!

I had to reinstall because the /etc/init.d/proftpd script was missing and it wasn't listening on any sockets.


ANy idea on how I can get apt-get to forget that the package is/was installed, or make it reinstall? I've tried doing apt-get install --reinstall proftpd, but it fails because it says it can't find /etc/init.d/proftpd


I tried installing pure-ftpd through apt-get this is what i get:

```

brian@ubuntu:~$ sudo apt-get install pure-ftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  pure-ftpd-common
Suggested packages:
  netkit-inetd openbsd-inetd xinetd
The following packages will be REMOVED:
  proftpd
The following NEW packages will be installed:
  pure-ftpd pure-ftpd-common
0 upgraded, 2 newly installed, 1 to remove and 85 not upgraded.
Need to get 0B/320kB of archives.
After unpacking 1430kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 28743 files and directories currently installed.)
Removing proftpd ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd (--remove):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
brian@ubuntu:~$

```

Please help!

Thanks,

Brian

---

### Post by weaverryan on 2008-02-01
I've never tried it before, but what about the purge command?
```

sudo aptitude purge proftpd
```

The normal remove leave configuration files, purge, apparently, does not

---

### Post by briancastellanos on 2008-02-04
I tried purge, but it's still throwing the same response:

> 
brian@ubuntu:~$ sudo aptitude purge proftpd
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  dbus gnome-media-common libcairo2 libcupsys2 libcurl3 libfreetype6 libgl1-mesa-glx libgnome-media0 libmetacity0 libperl5.8 libpng12-0 libsvn1 libt1-5
  libxfont1 linux-image-server mesa-utils metacity-common openssh-server openssl python-subversion samba-common subversion tcpdump
The following packages have been kept back:
  apache2 apache2-mpm-prefork apache2-src apache2-utils apache2.2-common bind9 bind9-doc bind9-host bsdutils curl dnsutils e2fslibs e2fsprogs file
  iptables libapache2-mod-perl2 libapache2-svn libbind9-0 libblkid1 libcomerr2 libdbus-1-3 libdns22 libisc11 libisccc0 libisccfg1 libkrb53 liblwres9
  libmagic1 libmysqlclient15off libpcre3 libpq5 libss2 libssl0.9.8 libuuid1 libwrap0 libxml2 linux-server mount mysql-client-5.0 mysql-common
  mysql-server mysql-server-5.0 openssh-client perl perl-base perl-modules python python-minimal python2.5 python2.5-minimal rsync samba smbclient smbfs
  ssh tar tzdata update-manager-core util-linux util-linux-locales vim-common vim-tiny
The following packages will be REMOVED:
  proftpd{p}
0 packages upgraded, 0 newly installed, 1 to remove and 85 not upgraded.
Need to get 0B of archives. After unpacking 2331kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 28743 files and directories currently installed.)
Removing proftpd ...
invoke-rc.d: unknown initscript, /etc/init.d/proftpd not found.
dpkg: error processing proftpd (--purge):
 subprocess pre-removal script returned error exit status 100
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
brian@ubuntu:~$


Does anyone else have any other ideas? I'd really appreciate it..

Thanks,

---

