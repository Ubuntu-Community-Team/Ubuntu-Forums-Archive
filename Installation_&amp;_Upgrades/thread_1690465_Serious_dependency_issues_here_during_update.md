---
title: "Serious dependency issues here during update"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by scruff on 2011-02-18
Any clues as to how I got in this state? I allowed something like 100 updates this morning and these packages won't complete:

```

[root.bitwise: /home/sean]$ apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
17 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up rsyslog (4.2.0-2ubuntu8.1) ...
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up grub-pc (1.98-1ubuntu10) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.7) ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up nfs-common (1:1.2.0-4ubuntu4.1) ...
dpkg: error processing nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cgi (5.3.2-1ubuntu4.7) ...
No apport report written because MaxReports is reached already
                                                              dpkg: error processing php5-cgi (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.2-1ubuntu4.7) | libapache2-mod-php5filter (>= 5.3.2-1ubuntu4.7) | php5-cgi (>= 5.3.2-1ubuntu4.7); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not configured yet.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cli (5.3.2-1ubuntu4.7) ...
No apport report written because MaxReports is reached already
                                                              dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php5-curl:
 php5-curl depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-curl (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php5-pgsql:
 php5-pgsql depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-pgsql (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.3) ...
No apport report written because MaxReports is reached already
                                                              dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.3); however:
  Package samba-common is not configured yet.
 samba depends on samba-common-bin; however:
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                    Package samba-common-bin is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-smbpass:
 libpam-smbpass depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.3); however:
  Package samba-common is not configured yet.
dpkg: error processing libpam-smbpass (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 rsyslog
 grub-pc
 libapache2-mod-php5
 nfs-common
 nfs-kernel-server
 php5-cgi
 php5
 php5-cli
 php5-curl
 php5-gd
 php5-mysql
 php5-pgsql
 samba-common
 samba-common-bin
 samba
 smbclient
 libpam-smbpass
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by zvacet on 2011-02-19
```
sudo dpkg -configure -a
sudo apt-get -f install
```

---

### Post by scruff on 2011-02-21
Same result: 

```

[root.bitwise: old_kernel_****]$ dpkg --configure -a

Setting up nfs-common (1:1.2.0-4ubuntu4.1) ...
dpkg: error processing nfs-common (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up php5-cgi (5.3.2-1ubuntu4.7) ...
dpkg: error processing php5-cgi (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.3) ...
dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of nfs-kernel-server:
 nfs-kernel-server depends on nfs-common (>= 1:1.0.8-1); however:
  Package nfs-common is not configured yet.
dpkg: error processing nfs-kernel-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.3); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up grub-pc (1.98-1ubuntu10) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
Setting up php5-cli (5.3.2-1ubuntu4.7) ...
dpkg: error processing php5-cli (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up libapache2-mod-php5 (5.3.2-1ubuntu4.7) ...
dpkg: error processing libapache2-mod-php5 (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.3.2-1ubuntu4.7) | libapache2-mod-php5filter (>= 5.3.2-1ubuntu4.7) | php5-cgi (>= 5.3.2-1ubuntu4.7); however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is not configured yet.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (4.2.0-2ubuntu8.1) ...
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.3); however:
  Package samba-common is not configured yet.
 samba depends on samba-common-bin; however:
  Package samba-common-bin is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-pgsql:
 php5-pgsql depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-pgsql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-smbpass:
 libpam-smbpass depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.3); however:
  Package samba-common is not configured yet.
dpkg: error processing libpam-smbpass (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-curl:
 php5-curl depends on phpapi-20090626+lfs; however:
  Package phpapi-20090626+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cli which provides phpapi-20090626+lfs is not configured yet.
  Package php5-cgi which provides phpapi-20090626+lfs is not configured yet.
dpkg: error processing php5-curl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nfs-common
 php5-cgi
 samba-common
 nfs-kernel-server
 smbclient
 grub-pc
 samba-common-bin
 php5-cli
 libapache2-mod-php5
 php5
 rsyslog
 php5-mysql
 samba
 php5-pgsql
 libpam-smbpass
 php5-gd
 php5-curl

```

---

