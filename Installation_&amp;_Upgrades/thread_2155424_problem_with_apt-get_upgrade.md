---
title: "problem with apt-get upgrade"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by amrnegm on 2013-06-18
when I run ```
sudo apt-get upgrade
```, the following error rises

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mysql-client-5.5 mysql-server-5.5 mysql-server-core-5.5
The following packages will be upgraded:
  accountsservice apport apt apt-transport-https apt-utils aptitude bash bash-completion bind9-host curl dbus dmsetup dnsutils icedtea-6-jre-cacao
  icedtea-6-jre-jamvm iptables isc-dhcp-client isc-dhcp-common language-selector-common libaccountsservice0 libapt-inst1.4 libapt-pkg4.12 libasound2
  libbind9-80 libc-bin libc-dev-bin libc6 libc6-dev libcups2 libcupsimage2 libcurl3 libcurl3-gnutls libdbus-1-3 libdevmapper1.02.1 libdns81
  libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgnutls26 libisc83 libisccc80 libisccfg82
  liblwres80 libmysqlclient-dev libmysqlclient18 libnspr4 libnss3 libnss3-1d libplymouth2 libservlet2.5-java libssl-dev libssl-doc libssl1.0.0
  libtiff4 libtomcat6-java libudev0 libx11-6 libx11-data libx11-xcb1 libxcb-glx0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1 libxext6
  libxfixes3 libxi6 libxinerama1 libxml2 libxrender1 libxslt1.1 libxt6 libxtst6 libxv1 libxxf86dga1 libxxf86vm1 linux-libc-dev multiarch-support
  mysql-client mysql-client-core-5.5 mysql-common mysql-server nginx nginx-common nginx-full openjdk-6-jre-headless openjdk-6-jre-lib openssh-client
  openssh-server openssl perl perl-base perl-modules plymouth plymouth-theme-ubuntu-text python-apport python-apt python-apt-common python-mysqldb
  python-paramiko python-problem-report rsyslog tomcat6 tomcat6-admin tomcat6-common tomcat6-docs tomcat6-examples udev
112 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/88.4 MB of archives.
After this operation, 204 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg-deb: error: subprocess tar was killed by signal (Segmentation fault), core dumped
dpkg: error processing /var/cache/apt/archives/bash_4.2-2ubuntu2.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.2-2ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

EDIT:
When I run:
```
[COLOR=#000000]sudo apt-get install --reinstall tar[/COLOR]
```
 it outputs:
```
dpkg-deb: error: subprocess tar was killed by signal (Segmentation fault), core dumpeddpkg: error processing /var/cache/apt/archives/tar_1.26-4ubuntu1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.26-4ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by Cheesemill on 2013-06-18
Try...
```
sudo apt-get clean && sudo apt-get upgrade
```

It looks like the bash_4.2-2ubuntu2.1_i386.deb package on your system is corrupted.

---

### Post by amrnegm on 2013-06-18
> **Cheesemill said:**
> Try...
```
sudo apt-get clean && sudo apt-get upgrade
```

It looks like the bash_4.2-2ubuntu2.1_i386.deb package on your system is corrupted.

I tried it, but it outputs the same error

---

### Post by Bashing-om on 2013-06-18
amrnegm;
That is odd as "apt-get clean" should have cleaned out the /archive ...what results then this code:
```
dpkg --contents /var/cache/apt/archives/[COLOR=#000000][FONT=Ubuntu Mono]bash_4.2-2ubuntu2.1_i386.deb[/FONT][/COLOR]
```

[INDENT][INDENT]sometimes I wonder, and other times I just do not know[/INDENT][/INDENT]

---

### Post by hamishmb on 2013-06-18
It appears that tar segfaulted. This is quite unusual. Try: sudo apt-get install --reinstall tar

---

### Post by amrnegm on 2013-06-19
when I run the command:
```
[COLOR=#000000][FONT=Ubuntu Mono]dpkg --contents /var/cache/apt/archives/[/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono][FONT=Ubuntu Mono]bash_4.2-2ubuntu2.1_i386.deb[/FONT][/FONT][/COLOR][/COLOR]
```
it outputs:
```
dpkg-deb: error: subprocess tar was killed by signal (Segmentation fault), core dumped
```

---

### Post by Bashing-om on 2013-06-20
[COLOR=#000000]amrnegm; Hey ![/COLOR]

I have given some thought...what results:
```

ls -ld /var/cache/apt/archives/[COLOR=#000000]bash_4.2-2ubuntu2.1_i386.deb ##just to see what happens.[/COLOR]
sudo rm -f /var/cache/apt/archives/[COLOR=#000000]bash_4.2-2ubuntu2.1_i386.deb ##remove it as it is corrupted.
sudo apt-get install --reinstall bash
[/COLOR]
```[COLOR=#000000][INDENT=2]
no harm in try'n

[/INDENT]

[/COLOR]

---

### Post by amrnegm on 2013-06-21
thanks [FONT=arial narrow][B][COLOR=#000000][Bashing-om]("http://ubuntuforums.org/member.php?u=1111508"), 
[/COLOR][/B][/FONT]
when I try your suggestion it outputs the following error:
```
dpkg-deb: error: subprocess tar was killed by signal (Segmentation fault), core dumped
dpkg: error processing /var/cache/apt/archives/bash_4.2-2ubuntu2.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bash_4.2-2ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I think the problem is with tar itself, since it outputs the following error for just typing 'tar' in the shell:
```
Segmentation fault (core dumped)
```
I tried to install tar itself, but nothing changed.

---

### Post by Bashing-om on 2013-06-21
[COLOR=#000000]amrnegm; 

Ok, let's see what the package manager has to say about "tar" :
```
dpkg -l tar
``` will give a system status of that package.

Truly can not do much if "tar" is broke !
[/COLOR][INDENT=3][COLOR=#000000]
regards

[/COLOR][/INDENT]

---

