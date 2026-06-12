---
title: "Troubleshooting 10.04 upgrading"
date: 2014-10-02
forum: Installation &amp; Upgrades
---

### Post by ChChu on 2014-10-02
Hello Ubuntu Community,

I'm reaching out for assistance, as I'm stuck finding why I can't update\upgrade my 10.04.2 LTS Lucid Lynx.

I've done sudo apt-get update && apt-get upgrade and I get the following output:
```
~# apt-get updateIgn http://ca.archive.ubuntu.com lucid Release.gpg
Ign http://ca.archive.archive.ubuntu.com lucid-security Release.gpg
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_CA
Ign http://ca.archive.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_CA
Ign http://ca.archive.ubuntu.com lucid-updates Release.gpg
Ign http://ca.archive.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_CA
Ign http://ca.archive.archive.ubuntu.com lucid-security Release
Ign http://ca.archive.ubuntu.com lucid-security Release.gpg
Ign http://ca.archive.ubuntu.com lucid Release
Ign http://ca.archive.archive.ubuntu.com lucid-security/main Packages
Ign http://ca.archive.ubuntu.com lucid-updates Release
Ign http://ca.archive.archive.ubuntu.com lucid-security/restricted Packages
Ign http://ca.archive.ubuntu.com lucid-security Release
Ign http://ca.archive.ubuntu.com lucid/main Packages
Ign http://ca.archive.archive.ubuntu.com lucid-security/main Packages
Ign http://ca.archive.ubuntu.com lucid/restricted Packages
Ign http://ca.archive.ubuntu.com lucid/main Sources
Ign http://ca.archive.archive.ubuntu.com lucid-security/restricted Packages
Ign http://ca.archive.ubuntu.com lucid/restricted Sources
Err http://ca.archive.archive.ubuntu.com lucid-security/main Packages
  503  Service Unavailable [IP: 91.189.92.200 80]
Ign http://ca.archive.ubuntu.com lucid-updates/main Packages
Ign http://ca.archive.ubuntu.com lucid-updates/restricted Packages
Err http://ca.archive.archive.ubuntu.com lucid-security/restricted Packages
  503  Service Unavailable [IP: 91.189.92.200 80]
Ign http://ca.archive.ubuntu.com lucid-updates/main Sources
Ign http://ca.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://ca.archive.ubuntu.com lucid-security/main Sources
Ign http://ca.archive.ubuntu.com lucid-security/restricted Sources
Ign http://ca.archive.ubuntu.com lucid/main Packages
Ign http://ca.archive.ubuntu.com lucid/restricted Packages
Ign http://ca.archive.ubuntu.com lucid/main Sources
Ign http://ca.archive.ubuntu.com lucid/restricted Sources
Ign http://ca.archive.ubuntu.com lucid-updates/main Packages
Ign http://ca.archive.ubuntu.com lucid-updates/restricted Packages
Ign http://ca.archive.ubuntu.com lucid-updates/main Sources
Ign http://ca.archive.ubuntu.com lucid-updates/restricted Sources
Ign http://ca.archive.ubuntu.com lucid-security/main Sources
Ign http://ca.archive.ubuntu.com lucid-security/restricted Sources
Err http://ca.archive.ubuntu.com lucid/main Packages
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid/restricted Packages
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid/main Sources
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid/restricted Sources
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid-updates/main Packages
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid-updates/restricted Packages
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid-updates/main Sources
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid-updates/restricted Sources
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid-security/main Sources
  503  Service Unavailable [IP: 91.189.92.201 80]
Err http://ca.archive.ubuntu.com lucid-security/restricted Sources
  503  Service Unavailable [IP: 91.189.92.201 80]
W: Failed to fetch http://ca.archive.archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-amd64/Packages.gz  503  Service Unavailable [IP: 91.189.92.200 80]


W: Failed to fetch http://ca.archive.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-amd64/Packages.gz  503  Service Unavailable [IP: 91.189.92.200 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-amd64/Packages.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-amd64/Packages.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz  503  Service Unavailable [IP: 91.189.92.201 80]


W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz  503  Service Unavailable [IP: 91.189.92.201 80]


E: Some index files failed to download, they have been ignored, or old ones used instead.
```

```
~# sudo apt-get upgradeReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
The following packages will be upgraded:
  apparmor apparmor-utils apport apt apt-transport-https apt-utils aptitude base-files bind9-host byobu bzip2 ca-certificates ca-certificates-java cpp-4.4 cron dhcp3-client
  dhcp3-common dnsutils dpkg ecryptfs-utils gcc-4.4-base ghostscript ghostscript-x gnupg gnupg-curl gpgv grub-common grub-pc gs icedtea-6-jre-cacao ifenslave-2.6 initscripts
  insserv landscape-common language-pack-en language-pack-en-base libapparmor-perl libapparmor1 libbind9-60 libbz2-1.0 libc-bin libc6 libcap2 libcups2 libcupsimage2
  libcurl3-gnutls libdbus-1-3 libdbus-glib-1-2 libdns64 libecryptfs0 libexpat1 libfreetype6 libgc1c2 libgcc1 libgcrypt11 libglib2.0-0 libgnutls26 libgs8 libgssapi-krb5-2
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libisc60 libisccc60 libisccfg60 libjasper1 libjs-jquery libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2 liblwres60
  libnspr4-0d libnss3-1d libpam-modules libpam-runtime libpam0g libparted0debian1 libpcsclite1 libpng12-0 libpython2.6 libsndfile1 libssl0.9.8 libstdc++6 libtasn1-3 libtiff4
  libvorbis0a libvorbisenc2 libwbclient0 libx11-6 libx11-data libxcb-render0 libxcb1 libxext6 libxfont1 libxi6 libxml2 libxrender1 libxt6 libxtst6 linux-firmware logrotate
  lsb-base lsb-release ntpdate openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openssh-client openssh-server openssl parted perl perl-base perl-modules procps
  python-apport python-apt python-httplib2 python-lazr.restfulclient python-pam python-problem-report python-smartpm python-wadllib python2.6 python2.6-minimal rsync samba
  samba-common samba-common-bin smbclient smbfs ssh sudo sysv-rc sysvinit-utils tzdata tzdata-java update-manager-core update-notifier-common vim vim-common vim-runtime
  vim-tiny wpasupplicant x11-common
146 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 142MB of archives.
After this operation, 4,653kB of additional disk space will be used.
Do you want to continue [Y/n]?Y
```
```
WARNING: The following packages cannot be authenticated!  libpam-modules base-files libc-bin libc6 gcc-4.4-base libgcc1 cpp-4.4 libstdc++6 tzdata-java tzdata grub-pc lsb-base libfreetype6 grub-common dpkg perl-modules bzip2
  libbz2-1.0 perl perl-base language-pack-en language-pack-en-base x11-common apt libssl0.9.8 libpam-runtime libpam0g libpython2.6 python2.6 python2.6-minimal apt-utils
  aptitude openssl ca-certificates cron dhcp3-client dhcp3-common gpgv gnupg libgcrypt11 libtasn1-3 libgnutls26 libk5crypto3 libgssapi-krb5-2 libkrb5-3 libkrb5support0
  libldap-2.4-2 libcurl3-gnutls gnupg-curl libcap2 logrotate lsb-release ntpdate sudo vim-tiny vim vim-runtime vim-common insserv sysvinit-utils sysv-rc initscripts
  libglib2.0-0 procps apparmor libapparmor1 libapparmor-perl apparmor-utils apt-transport-https libxml2 bind9-host dnsutils libisc60 libdns64 libisccc60 libisccfg60 liblwres60
  libbind9-60 libgc1c2 libxcb1 libx11-data libx11-6 libxext6 openssh-server openssh-client libparted0debian1 parted python-apt rsync update-manager-core python-problem-report
  python-apport apport byobu icedtea-6-jre-cacao openjdk-6-jre-headless openjdk-6-jre-lib libcups2 libnspr4-0d libnss3-1d libpcsclite1 ca-certificates-java libecryptfs0
  ecryptfs-utils libpng12-0 libtiff4 libcupsimage2 ghostscript libgs8 libxt6 ghostscript-x ifenslave-2.6 landscape-common libdbus-1-3 libdbus-glib-1-2 libexpat1
  libgtk2.0-common libjasper1 libxi6 libxrender1 libgtk2.0-0 libgtk2.0-bin libjs-jquery libvorbis0a libvorbisenc2 libsndfile1 smbclient smbfs samba samba-common
  samba-common-bin libwbclient0 libxcb-render0 libxfont1 libxtst6 linux-firmware openjdk-6-jre python-httplib2 python-wadllib python-lazr.restfulclient python-pam
  python-smartpm ssh update-notifier-common wpasupplicant gs
Install these packages without verification [y/N]?Y
```
```
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libpam-modules 1.1.1-2ubuntu5.6  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main base-files 5.0.0ubuntu20.10.04.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libc-bin 2.11.1-0ubuntu7.12
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libc6 2.11.1-0ubuntu7.12
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main gcc-4.4-base 4.4.3-4ubuntu5.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgcc1 1:4.4.3-4ubuntu5.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main cpp-4.4 4.4.3-4ubuntu5.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libstdc++6 4.4.3-4ubuntu5.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main tzdata-java 2012e-0ubuntu0.10.04
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main tzdata 2012e-0ubuntu0.10.04
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-pc 1.98-1ubuntu13
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main lsb-base 4.0-0ubuntu8.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libfreetype6 2.3.11-1ubuntu2.7
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main grub-common 1.98-1ubuntu13
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main dpkg 1.15.5.6ubuntu4.6
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main perl-modules 5.10.1-8ubuntu2.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main bzip2 1.0.5-4ubuntu0.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libbz2-1.0 1.0.5-4ubuntu0.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main perl 5.10.1-8ubuntu2.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main perl-base 5.10.1-8ubuntu2.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main language-pack-en 1:10.04+20110931
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main language-pack-en-base 1:10.04+20110931
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main x11-common 1:7.5+5ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main apt 0.7.25.3ubuntu9.14
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libssl0.9.8 0.9.8k-7ubuntu8.15
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libpam-runtime 1.1.1-2ubuntu5.6
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libpam0g 1.1.1-2ubuntu5.6
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libpython2.6 2.6.5-1ubuntu6.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python2.6 2.6.5-1ubuntu6.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python2.6-minimal 2.6.5-1ubuntu6.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main apt-utils 0.7.25.3ubuntu9.14
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main aptitude 0.4.11.11-1ubuntu10lucid1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main openssl 0.9.8k-7ubuntu8.15
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ca-certificates 20090814ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main cron 3.0pl1-106ubuntu7
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main dhcp3-client 3.1.3-2ubuntu3.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main dhcp3-common 3.1.3-2ubuntu3.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main gpgv 1.4.10-2ubuntu1.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main gnupg 1.4.10-2ubuntu1.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgcrypt11 1.4.4-5ubuntu2.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libtasn1-3 2.4-1ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgnutls26 2.8.5-2ubuntu0.4
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libk5crypto3 1.8.1+dfsg-2ubuntu0.11
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.11
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5-3 1.8.1+dfsg-2ubuntu0.11
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5support0 1.8.1+dfsg-2ubuntu0.11
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libldap-2.4-2 2.4.21-0ubuntu5.7
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libcurl3-gnutls 7.19.7-1ubuntu1.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main gnupg-curl 1.4.10-2ubuntu1.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libcap2 1:2.17-2ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main logrotate 3.7.8-4ubuntu2.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main lsb-release 4.0-0ubuntu8.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ntpdate 1:4.2.4p8+dfsg-1ubuntu2.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main sudo 1.7.2p1-1ubuntu5.6
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main vim-tiny 2:7.2.330-1ubuntu3.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main vim 2:7.2.330-1ubuntu3.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main vim-runtime 2:7.2.330-1ubuntu3.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main vim-common 2:7.2.330-1ubuntu3.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main insserv 1.12.0-14ubuntu0.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main sysvinit-utils 2.87dsf-4ubuntu17.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main sysv-rc 2.87dsf-4ubuntu17.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main initscripts 2.87dsf-4ubuntu17.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libglib2.0-0 2.24.1-0ubuntu2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main procps 1:3.2.8-1ubuntu4.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main apparmor 2.5.1-0ubuntu0.10.04.4
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libapparmor1 2.5.1-0ubuntu0.10.04.4
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libapparmor-perl 2.5.1-0ubuntu0.10.04.4
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main apparmor-utils 2.5.1-0ubuntu0.10.04.4
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main apt-transport-https 0.7.25.3ubuntu9.14
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxml2 2.7.6.dfsg-1ubuntu1.8
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main bind9-host 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main dnsutils 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libisc60 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libdns64 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libisccc60 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libisccfg60 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main liblwres60 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libbind9-60 1:9.7.0.dfsg.P1-1ubuntu0.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgc1c2 1:6.8-1.2ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxcb1 1.5-2ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libx11-data 2:1.3.2-1ubuntu3.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libx11-6 2:1.3.2-1ubuntu3.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxext6 2:1.1.1-2ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main openssh-server 1:5.3p1-3ubuntu7
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main openssh-client 1:5.3p1-3ubuntu7
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libparted0debian1 2.2-5ubuntu5.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main parted 2.2-5ubuntu5.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-apt 0.7.94.2ubuntu6.4
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main rsync 3.0.7-1ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main update-manager-core 1:0.134.12.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-problem-report 1.13.3-0ubuntu2.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-apport 1.13.3-0ubuntu2.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main apport 1.13.3-0ubuntu2.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main byobu 2.68-0ubuntu1.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main icedtea-6-jre-cacao 6b27-1.12.5-0ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main openjdk-6-jre-headless 6b27-1.12.5-0ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main openjdk-6-jre-lib 6b27-1.12.5-0ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libcups2 1.4.3-1ubuntu1.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libnspr4-0d 4.9.5-0ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libnss3-1d 3.14.3-0ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libpcsclite1 1.5.3-1ubuntu4.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ca-certificates-java 20100406ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libecryptfs0 83-0ubuntu3.2.10.04.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ecryptfs-utils 83-0ubuntu3.2.10.04.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libpng12-0 1.2.42-1ubuntu2.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libtiff4 3.9.2-2ubuntu0.13
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libcupsimage2 1.4.3-1ubuntu1.9
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ghostscript 8.71.dfsg.1-0ubuntu5.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgs8 8.71.dfsg.1-0ubuntu5.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxt6 1:1.0.7-1ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ghostscript-x 8.71.dfsg.1-0ubuntu5.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ifenslave-2.6 1.1.0-14ubuntu2.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main landscape-common 12.05-0ubuntu1.10.04
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libdbus-1-3 1.2.16-2ubuntu4.7
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libdbus-glib-1-2 0.84-1ubuntu0.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libexpat1 2.0.1-7ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtk2.0-common 2.20.1-0ubuntu2.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libjasper1 1.900.1-7ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxi6 2:1.3-3ubuntu0.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxrender1 1:0.9.5-1ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtk2.0-0 2.20.1-0ubuntu2.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libgtk2.0-bin 2.20.1-0ubuntu2.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libjs-jquery 1.3.3-2ubuntu1.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libvorbis0a 1.2.3-3ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libvorbisenc2 1.2.3-3ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libsndfile1 1.0.21-2ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main smbclient 2:3.4.7~dfsg-1ubuntu3.10
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main smbfs 2:3.4.7~dfsg-1ubuntu3.10
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main samba 2:3.4.7~dfsg-1ubuntu3.10
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main samba-common 2:3.4.7~dfsg-1ubuntu3.10
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main samba-common-bin 2:3.4.7~dfsg-1ubuntu3.10
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libwbclient0 2:3.4.7~dfsg-1ubuntu3.10
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxcb-render0 1.5-2ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxfont1 1:1.4.1-1ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main libxtst6 2:1.1.0-2ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main linux-firmware 1.34.14
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main openjdk-6-jre 6b27-1.12.5-0ubuntu0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-httplib2 0.7.2-1ubuntu2~0.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-wadllib 1.1.4-1ubuntu1.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-lazr.restfulclient 0.9.11-1ubuntu1.3
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-pam 0.4.2-12.1ubuntu1.10.04.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main python-smartpm 1.2-5ubuntu0.2
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main ssh 1:5.3p1-3ubuntu7
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main update-notifier-common 0.99.3ubuntu0.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main wpasupplicant 0.6.9-3ubuntu3.1
  503  Service Unavailable [IP: 91.189.88.153 80]
Err http://ca.archive.ubuntu.com/ubuntu/ lucid-updates/main gs 8.71.dfsg.1-0ubuntu5.5
  503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.1.1-2ubuntu5.6_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_5.0.0ubuntu20.10.04.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.11.1-0ubuntu7.12_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.11.1-0ubuntu7.12_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/gcc-4.4-base_4.4.3-4ubuntu5.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libgcc1_4.4.3-4ubuntu5.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/cpp-4.4_4.4.3-4ubuntu5.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.4/libstdc++6_4.4.3-4ubuntu5.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2012e-0ubuntu0.10.04_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2012e-0ubuntu0.10.04_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.98-1ubuntu13_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lsb/lsb-base_4.0-0ubuntu8.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.11-1ubuntu2.7_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98-1ubuntu13_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.6_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.1-8ubuntu2.3_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.5-4ubuntu0.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.5-4ubuntu0.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.10.1-8ubuntu2.3_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.10.1-8ubuntu2.3_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_10.04+20110931_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_10.04+20110931_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x11-common_7.5+5ubuntu1.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.14_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.15_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.1.1-2ubuntu5.6_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.1.1-2ubuntu5.6_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.5-1ubuntu6.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.5-1ubuntu6.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.5-1ubuntu6.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.14_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/aptitude/aptitude_0.4.11.11-1ubuntu10lucid1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.15_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates/ca-certificates_20090814ubuntu0.10.04.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/c/cron/cron_3.0pl1-106ubuntu7_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.1.3-2ubuntu3.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.1.3-2ubuntu3.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gpgv_1.4.10-2ubuntu1.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg_1.4.10-2ubuntu1.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgcrypt11/libgcrypt11_1.4.4-5ubuntu2.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libt/libtasn1-3/libtasn1-3_2.4-1ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.8.5-2ubuntu0.4_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-2ubuntu0.11_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.11_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-2ubuntu0.11_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-2ubuntu0.11_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.21-0ubuntu5.7_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.19.7-1ubuntu1.3_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnupg/gnupg-curl_1.4.10-2ubuntu1.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libc/libcap2/libcap2_2.17-2ubuntu1.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/logrotate/logrotate_3.7.8-4ubuntu2.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lsb/lsb-release_4.0-0ubuntu8.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p8+dfsg-1ubuntu2.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.2p1-1ubuntu5.6_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-tiny_7.2.330-1ubuntu3.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim_7.2.330-1ubuntu3.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-runtime_7.2.330-1ubuntu3.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/v/vim/vim-common_7.2.330-1ubuntu3.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/i/insserv/insserv_1.12.0-14ubuntu0.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysvinit-utils_2.87dsf-4ubuntu17.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysv-rc_2.87dsf-4ubuntu17.5_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu17.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.24.1-0ubuntu2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.8-1ubuntu4.3_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.1-0ubuntu0.10.04.4_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.5.1-0ubuntu0.10.04.4_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.5.1-0ubuntu0.10.04.4_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.5.1-0ubuntu0.10.04.4_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.14_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.6.dfsg-1ubuntu1.8_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns64_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.0.dfsg.P1-1ubuntu0.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libg/libgc/libgc1c2_6.8-1.2ubuntu1.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.5-2ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-data_1.3.2-1ubuntu3.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libx11/libx11-6_1.3.2-1ubuntu3.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxext/libxext6_1.1.1-2ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-server_5.3p1-3ubuntu7_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_5.3p1-3ubuntu7_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/parted/libparted0debian1_2.2-5ubuntu5.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/parted/parted_2.2-5ubuntu5.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.7.94.2ubuntu6.4_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_3.0.7-1ubuntu1.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.134.12.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.13.3-0ubuntu2.2_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.13.3-0ubuntu2.2_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.13.3-0ubuntu2.2_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/byobu/byobu_2.68-0ubuntu1.2_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/icedtea-6-jre-cacao_6b27-1.12.5-0ubuntu0.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-headless_6b27-1.12.5-0ubuntu0.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre-lib_6b27-1.12.5-0ubuntu0.10.04.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.3-1ubuntu1.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.9.5-0ubuntu0.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.14.3-0ubuntu0.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pcsc-lite/libpcsclite1_1.5.3-1ubuntu4.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/c/ca-certificates-java/ca-certificates-java_20100406ubuntu1.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/e/ecryptfs-utils/libecryptfs0_83-0ubuntu3.2.10.04.3_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/e/ecryptfs-utils/ecryptfs-utils_83-0ubuntu3.2.10.04.3_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.42-1ubuntu2.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.2-2ubuntu0.13_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.3-1ubuntu1.9_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.71.dfsg.1-0ubuntu5.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.71.dfsg.1-0ubuntu5.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt6_1.0.7-1ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.71.dfsg.1-0ubuntu5.5_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/i/ifenslave-2.6/ifenslave-2.6_1.1.0-14ubuntu2.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/landscape-client/landscape-common_12.05-0ubuntu1.10.04_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.2.16-2ubuntu4.7_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dbus-glib/libdbus-glib-1-2_0.84-1ubuntu0.3_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1_2.0.1-7ubuntu1.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.20.1-0ubuntu2.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-7ubuntu0.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxi/libxi6_1.3-3ubuntu0.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxrender/libxrender1_0.9.5-1ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.20.1-0ubuntu2.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.20.1-0ubuntu2.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/j/jquery/libjs-jquery_1.3.3-2ubuntu1.2_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.2.3-3ubuntu1.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.2.3-3ubuntu1.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.21-2ubuntu0.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.7~dfsg-1ubuntu3.10_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.4.7~dfsg-1ubuntu3.10_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.4.7~dfsg-1ubuntu3.10_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.7~dfsg-1ubuntu3.10_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.7~dfsg-1ubuntu3.10_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.10_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-render0_1.5-2ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.4.1-1ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxtst/libxtst6_1.1.0-2ubuntu0.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.34.14_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jre_6b27-1.12.5-0ubuntu0.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-httplib2/python-httplib2_0.7.2-1ubuntu2~0.10.04.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-wadllib/python-wadllib_1.1.4-1ubuntu1.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lazr.restfulclient/python-lazr.restfulclient_0.9.11-1ubuntu1.3_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/p/python-pam/python-pam_0.4.2-12.1ubuntu1.10.04.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/smart/python-smartpm_1.2-5ubuntu0.2_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh_5.3p1-3ubuntu7_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/u/update-notifier/update-notifier-common_0.99.3ubuntu0.1_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/w/wpasupplicant/wpasupplicant_0.6.9-3ubuntu3.1_amd64.deb 503  Service Unavailable [IP: 91.189.88.153 80]
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/gs_8.71.dfsg.1-0ubuntu5.5_all.deb 503  Service Unavailable [IP: 91.189.88.153 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
```

I'm still very new to linux operating systems so please bear with me. 
I validated this server has correct network config. 
Can ping internal and external. 
Played around with different repos (old-releases give me same result above)
Would appreciate any help. I've done some searching already on the forums and am drawing a blank. We're patching legacy boxes due to the shellshock bug that was posted in the media and management is requiring immediate re-mediation.

Thanks in advance!
Chu

---

### Post by gifford on 2014-10-02
Ubuntu 10.04 long ago reached it's end of life. It is no longer supported. You will have to
install a newer version.

---

### Post by ChChu on 2014-10-02
Hi Gifford,

Thank you for responding. I'm running on the server LTS release of 10.04.2 ([https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)).

Please correct me if I'm wrong.
```
~# lsb_release -aNo LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:        10.04
Codename:       lucid

```

---

### Post by gifford on 2014-10-02
I stand corrected...looks like the server version is good until April 2015.
Try changing to using the main repository and see if it will update.

---

### Post by ChChu on 2014-10-02
Hi Gifford,

When you mean editing my /apt/sources.list to the main repo... you mean http:\\archive.ubuntu.com ? Or only include the main repositories, minus the universe multiverse etc.. etc..

Copy of my sources.list:

```
## deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
#deb cdrom:[Ubuntu-Server 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted


#deb http://mirrors.ubuntu.com/mirrors.txt lucid main restricted universe multiverse
#deb http://mirrors.ubuntu.com/mirrors.txt lucid-updates main restricted universe multiverse
#deb http://mirrors.ubuntu.com/mirrors.txt lucid-backports main restricted universe multiverse
#deb http://mirrors.ubuntu.com/mirrors.txt lucid-security main restricted universe multiverse


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted


## EOL upgrade sources.list
# Required
#deb http://old-releases.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse


# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe
#deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid universe
#deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe
#deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
#deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse
#deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
#deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
#deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partn


deb http://ca.archive.archive.ubuntu.com/ubuntu/ lucid-security main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-security main restricted
#deb http://ca.archive.ubuntu.com/ubuntu/ lucid-security universe
#deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-security universe
#deb http://ca.archive.ubuntu.com/ubuntu/ lucid-security multiverse
#deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-security multiverse
```

---

### Post by ChChu on 2014-10-02
Hello again,

I've tried changing my sources.list to different mirrors and still same result. 

I'm able to use wget to download items. Any help will be appreciated.

---

### Post by gifford on 2014-10-02
Yes, change to download from main server.
Uncheck CDrom, see if that doesn't help.
Also, read this: [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

It appears the desktop for 10.04 is broken and there will be no attempt to fix it.

---

### Post by mörgæs on 2014-10-03
Sorry to say, but your server is in a bad shape. 146 packages in need of upgrade...

Besides the technical problems with the upgrade I suggest you focus on a policy for maintaining the installation in the future.

---

### Post by TheFu on 2014-10-03
I have one 10.04 server left too.
It has been patched consistently almost every Saturday morning during maintenance windows for years. I don't see these issues. It does not have any GUI installed and only 1 program that wasn't installed through Ubuntu repos (the main program/reason for the server). Installation of programs outside the repos increases the risks of incompatibilities over time and definitely increases the effort necessary to maintain any specific program from a .deb file or from source. If from .deb file(s), eventually, there will be be dependencies that conflict between that program and the rest of the OS installed programs. That often leads to "APT hell" or "RPM hell" where no packages can be updated regardless of the effort until the offending package is removed first.  About 2 months ago, I finally got a 10.04 physical server out of "APT hell" - by wiping and and putting a fresh 14.04 onto it.  There are still things on that system from the 10.04 days which I haven't got working again, but the main things were working the same day as the fresh install. 

If there is a GUI, THAT is likely the issue. Remove it.

When there are dependency issues, **aptitude** is smarter than apt-get for updates. Give that a try.
```
# aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```
Staying current with patches is important for server administration, just like having backups is.

---

### Post by ChChu on 2014-10-03
Hello again,

Thank you for the responses. This server does not have GUI installed, only terminal. I went through different http mirrors (probably like 80+) and decided to give one of the ftp mirrors a try... low and behold I was able to connect and download!

I know, SMH. I was recently promoted into a sys-admin and I've been handed to take care majority of our linux based systems. We have quite a few that are EOL. And continually maintaining these systems is something I hope to achieve.

Thank you for pointing me in the right direction. I certainly was about to give up!

---

### Post by mörgæs on 2014-10-03
Good, please mark the thread 'solved'.

---

