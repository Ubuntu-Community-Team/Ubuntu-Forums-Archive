---
title: "dpkg errors after installing 1404"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by pmheideman on 2014-04-20
after i upgraded to 14.04, i got a nasty error involving samba and dpkg, and now I can't install any software.  When I try to fix it through the software center, I get the following error message:
```
installArchives() failed: (Reading database ... (Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 461985 files and directories currently installed.)
Preparing to unpack .../samba-libs_2%3a4.1.6+dfsg-1ubuntu2_amd64.deb ...
secrets.tdb exists in /var/lib/samba and /var/lib/samba/private, aborting samba-libs preinst
rename one of them to allow the install/upgrade to continue
http://bugs.debian.org/726472
/var/lib/samba:
total 2204
drwxr-xr-x  7 root root         4096 Apr 17 20:10 .
drwxr-xr-x 82 root root         4096 Apr 18 17:08 ..
-rw-------  1 root root       421888 Jan 20  2013 account_policy.tdb
-rw-------  1 root root          696 Jan 20  2013 group_mapping.tdb
drwxr-x---  2 root root         4096 Jan  2 09:15 ntp_signd
-rw-------  1 root root       421888 Jan 20  2013 passdb.tdb
drwxr-xr-x  6 root root         4096 Jan  2 09:15 private
-rw-------  1 root root       528384 Mar 28 18:16 registry.tdb
-rw-------  1 root root       430080 Jan 20  2013 secrets.tdb
-rw-------  1 root root       421888 Jan 20  2013 share_info.tdb
drwxr-xr-x  3 root root         4096 Dec  9 01:00 sysvol
drwxrwx--T  2 root sambashare   4096 Jan 20  2013 usershares
drwxr-x---  2 root root         4096 Dec 14 16:14 winbindd_privileged


/var/lib/samba/private:
total 10472
drwxr-xr-x 6 root root    4096 Jan  2 09:15 .
drwxr-xr-x 7 root root    4096 Apr 17 20:10 ..
-rw------- 1 root root 1286144 Dec  9 01:00 hklm.ldb
-rw------- 1 root root 1286144 Dec  9 01:00 idmap.ldb
srwxrwxrwx 1 root root       0 Jan  2 09:15 ldapi
drwxr-x--- 2 root root    4096 Jan  2 09:15 ldap_priv
-r--r--r-- 1 root root     166 Dec 21 19:28 named.conf.update
-rw------- 1 root root 1286144 Dec  9 01:00 privilege.ldb
-rw------- 1 root root     696 Dec 14 16:13 randseed.tdb
-rw------- 1 root root 4251648 Dec  9 01:00 sam.ldb
drwx------ 2 root root    4096 Dec  9 01:00 sam.ldb.d
-rw------- 1 root root     696 Jan  2 09:15 schannel_store.tdb
-rw------- 1 root root 1286144 Dec  9 01:00 secrets.ldb
-rw------- 1 root root     696 Dec  9 01:00 secrets.tdb
-rw------- 1 root root 1286144 Dec  9 01:00 share.ldb
drwxr-xr-x 3 root root    4096 Dec 14 16:14 smbd.tmp
drwxr-xr-x 2 root root    4096 Dec 14 16:14 tls
dpkg: error processing archive /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of libsmbclient:amd64:
 libsmbclient:amd64 depends on samba-libs (= 2:4.1.6+dfsg-1ubuntu2); however:
  Package samba-libs:amd64 is not installed.


dpkg: error processing package libsmbclient:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-samba:
 python-samba depends on samba-libs (= 2:4.1.6+dfsg-1ubuntu2); however:
  Package samba-libs:amd64 is not installed.


dpkg: error processing package python-samba (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-smbc:
 python-smbc depends on libsmbclient (>= 2:4.0.3+dfsg1); however:
  Package libsmbclient:amd64 is not configured yet.


dpkg: error processing package python-smbc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on libsmbclient (>= 2:4.0.3+dfsg1); however:
  Package libsmbclient:amd64 is not configured yet.


dpkg: error processing package gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on gvfs-backends; however:
  Package gvfs-backends is not configured yet.



```

When I try to fix through terminal using sudo apt-get -f install, here's what I get:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  blt calligra-data calligra-libs calligrawords-common calligrawords-data
  icoutils k3b-data kde-runtime-data libaio1 libakonadi-kde4
  libakonadiprotocolinternals1 libamd2.2.0 libastro1 libbasicusageenvironment0
  libbibutils2 libboost-date-time1.53.0 libboost-filesystem1.53.0
  libboost-iostreams1.53.0 libboost-program-options1.53.0
  libboost-system1.53.0 libboost-test1.53.0 libcauchy0.0 libcddb2
  libcmis-0.3-3 libcrystalhd3 libdb5.1:i386 libdee-qt5-3 libdns99 libdvbpsi8
  libebackend-1.2-6 libebml3 libebml4 libedata-book-1.2-17 libedata-cal-1.2-20
  libexplain30 libfftw3-3 libfftw3-long3 libflac++6 libghc-citeproc-hs-data
  libglew1.8 libglewmx1.8 libgnutls28 libgps20 libgroupsock1 libgweather-3-3
  libhogweed2 libhud-client2 libk3b6 libkabc4 libkadm5clnt-mit8
  libkadm5srv-mit8 libkcal4 libkcalcore4 libkdb5-6 libkldap4 libkmime4
  libkpimutils4 libkresources4 libkrossui4 libkubuntu0 liblcms1:i386
  liblivemedia23 libllvm3.3 libllvm3.3:i386 libm2mml0.0 libmarblewidget18
  libmatroska5 libmatroska6 libmjpegutils-2.0-0 libmng1:i386
  libmpeg2encpp-2.0-0 libmplex2-2.0-0 libntrack-qt4-1 libntrack0
  libodfgen-0.0-0 libphononexperimental4 libpoppler43 libppl12 libprocps0
  libpython3.3 libpython3.3-minimal libpython3.3-stdlib libqapt2
  libqapt2-runtime libqextserialport1 libqpdf10 libqt53d5 libqt5location5
  libqt5v8-5 libqtlocation1 libquazip0 libresid-builder0c2a librhythmbox-core7
  libshp1 libsidplay2 libspnav0 libtar0 libtasn1-3:i386 libtasn1-3-dev
  libtcl8.5 libtk8.4 libtk8.5 libumfpack5.4.0 libupnp6 libusageenvironment1
  libva-x11-1 libwebp4 libwlocate0 libx264-123 libxcb-composite0
  libxcb-keysyms1 libxcb-sync0 libxcb-xv0 marble-data marble-plugins
  ntrack-module-libnl-0 oxygen-icon-theme plasma-scriptengine-javascript
  python-imaging-compat python3.3 python3.3-minimal shared-desktop-ontologies
  tcl8.5 tdb-tools tk8.4 tk8.5 ttf-marvosym
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba-libs
The following NEW packages will be installed:
  samba-libs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0 B/4,101 kB of archives.
After this operation, 18.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y


(Reading database ... 461985 files and directories currently installed.)
Preparing to unpack .../samba-libs_2%3a4.1.6+dfsg-1ubuntu2_amd64.deb ...
secrets.tdb exists in /var/lib/samba and /var/lib/samba/private, aborting samba-libs preinst
rename one of them to allow the install/upgrade to continue
http://bugs.debian.org/726472
/var/lib/samba:
total 2204
drwxr-xr-x  7 root root         4096 Apr 17 20:10 .
drwxr-xr-x 82 root root         4096 Apr 18 17:08 ..
-rw-------  1 root root       421888 Jan 20  2013 account_policy.tdb
-rw-------  1 root root          696 Jan 20  2013 group_mapping.tdb
drwxr-x---  2 root root         4096 Jan  2 09:15 ntp_signd
-rw-------  1 root root       421888 Jan 20  2013 passdb.tdb
drwxr-xr-x  6 root root         4096 Jan  2 09:15 private
-rw-------  1 root root       528384 Mar 28 18:16 registry.tdb
-rw-------  1 root root       430080 Jan 20  2013 secrets.tdb
-rw-------  1 root root       421888 Jan 20  2013 share_info.tdb
drwxr-xr-x  3 root root         4096 Dec  9 01:00 sysvol
drwxrwx--T  2 root sambashare   4096 Jan 20  2013 usershares
drwxr-x---  2 root root         4096 Dec 14 16:14 winbindd_privileged


/var/lib/samba/private:
total 10472
drwxr-xr-x 6 root root    4096 Jan  2 09:15 .
drwxr-xr-x 7 root root    4096 Apr 17 20:10 ..
-rw------- 1 root root 1286144 Dec  9 01:00 hklm.ldb
-rw------- 1 root root 1286144 Dec  9 01:00 idmap.ldb
srwxrwxrwx 1 root root       0 Jan  2 09:15 ldapi
drwxr-x--- 2 root root    4096 Jan  2 09:15 ldap_priv
-r--r--r-- 1 root root     166 Dec 21 19:28 named.conf.update
-rw------- 1 root root 1286144 Dec  9 01:00 privilege.ldb
-rw------- 1 root root     696 Dec 14 16:13 randseed.tdb
-rw------- 1 root root 4251648 Dec  9 01:00 sam.ldb
drwx------ 2 root root    4096 Dec  9 01:00 sam.ldb.d
-rw------- 1 root root     696 Jan  2 09:15 schannel_store.tdb
-rw------- 1 root root 1286144 Dec  9 01:00 secrets.ldb
-rw------- 1 root root     696 Dec  9 01:00 secrets.tdb
-rw------- 1 root root 1286144 Dec  9 01:00 share.ldb
drwxr-xr-x 3 root root    4096 Dec 14 16:14 smbd.tmp
drwxr-xr-x 2 root root    4096 Dec 14 16:14 tls
dpkg: error processing archive /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/samba-libs_2%3a4.1.6+dfsg-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by pmheideman on 2014-04-20
found the answer! [http://askubuntu.com/questions/449745/broken-dependency-after-upgrading-ubuntu-14-04](http://askubuntu.com/questions/449745/broken-dependency-after-upgrading-ubuntu-14-04)

---

### Post by Bashing-om on 2014-04-20
pmheideman; Hi !

You did good work ! Thanks for providing the soultion.
The package manager is pretty smart, huh, but will not presume what the aministrator of the system would dictate.

Please mark this thread solved, aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.
Top of post -> thread tools .

[INDENT][INDENT]were no step for a stepper
[/INDENT][/INDENT]

---

