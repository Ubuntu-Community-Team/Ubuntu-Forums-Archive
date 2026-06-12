---
title: "gcompris-data error during apt-get upgrade"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by Spleenie on 2006-09-25
```
 sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  amarok amarok-xine checkinstall linux-image-386
  linux-restricted-modules-386 totem
The following packages will be upgraded:
  automatix bind9-host bluefish dia-common dia-gnome dia-libs dnsutils
  firefox firefox-gnome-support flashplugin-nonfree gftp gftp-common
  gftp-gtk gftp-text gzip imagemagick k3b kdelibs-bin kdelibs-data
  kdelibs4c2a kdenetwork-filesharing kdenetwork-kfile-plugins kdnssd
  kopete kpf kppp krdc krfb ktorrent kubuntu-desktop kubuntu-docs
  libbind9-0 libdns21 libgnomecups1.0-1 libgnutls12 libisc11 libisccc0
  libisccfg1 libk3b2 liblwres9 libmagick9 libmysqlclient15off libnspr4
  libnss3 libruby1.8 libsmbclient libssl0.9.8 libtag1c2a libtagc0
  libtheora0 libtotem-plparser1 libtunepimp2c2a libxfont1 libxine-main1
  linux-386 linux-restricted-modules-common mozilla-mplayer
  mozilla-thunderbird mysql-common openoffice.org-kde openssl pmount
  ubuntu-base ubuntu-desktop wine xchat xchat-common xserver-xorg-core
68 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/89.5MB of archives.
After unpacking 12.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libmagick9_6%3a6.2.4.5-0.6ubuntu0.2_i386.deb (--unpack):
 files list file for package `gcompris-data' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libmagick9_6%3a6.2.4.5-0.6ubuntu0.2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anyone understand this error or is getting it themselves?

Something to do with imagemagick or gcompris-data. I am not sure but it is preventing me from upgrading/installing.

Thanks in advance :)

Spleenie

---

