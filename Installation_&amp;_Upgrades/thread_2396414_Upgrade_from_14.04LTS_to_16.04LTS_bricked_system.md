---
title: "Upgrade from 14.04LTS to 16.04LTS bricked system"
date: 2018-07-15
forum: Installation &amp; Upgrades
---

### Post by vpotesil on 2018-07-15
I finally decided to upgrade my system to 16.04 LTS, however the upgrade process finished but reported some errors and now I have system that has broken dependencies and not working Xorg or network.

Can someone advice how to fix this dependency error? I should have only all default repositories for 16.04 enabled right now.

Running apt upgrade:
```
 $ sudo apt upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 acestream-player : Depends: acestream-player-data (>= 3.0.2) but it is not installable
 baloo : Depends: baloo-kf5 (>= 5.18.0) but it is not installed
 kate : Depends: plasma-framework but it is not installed
        Depends: libgit2-24 (>= 0.24.0) but it is not installed
        Depends: libkf5itemmodels5 (>= 4.96.0) but it is not installed
        Depends: libkf5newstuff5 (>= 5.10.0) but it is not installed
 katepart : Depends: libkatepartinterfaces4 (= 4:4.14.3-0ubuntu4) but 4:4.13.3-0ubuntu0.1 is installed
            Depends: libkdecore5 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
            Depends: libkdeui5 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
            Depends: libkio5 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
            Depends: libkparts4 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
            Depends: libktexteditor4 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
 kde-workspace : Depends: kde-workspace-bin (>= 4:4.11.11-0ubuntu0.2) but it is not installable
 kdelibs-bin : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
               Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
               Depends: libkjsapi4 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
               Depends: libkjsembed4 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 kdelibs5-plugins : Depends: libkde3support4 (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
                    Depends: libkemoticons4 (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
                    Depends: libkfile4 (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
                    Depends: libkrosscore4 (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
                    Depends: kdelibs-bin (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
 kscreensaver-xsavers : Depends: kde-workspace-bin but it is not installable
                        Recommends: kscreensaver (= 4:4.13.3-0ubuntu0.1) but it is not installable
 libapparmor-perl : Depends: perlapi-5.18.2 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.18.1 but it is not installable
 libavformat57 : Depends: libgnutls28 (>= 3.2.10-0) but it is not installable
 libc-dev-bin : Depends: libc6 (< 2.20) but 2.23-0ubuntu10 is installed
 libc6-dev : Depends: libc6 (= 2.19-0ubuntu6.14) but 2.23-0ubuntu10 is installed
 libc6-i386 : Depends: libc6 (= 2.19-0ubuntu6.14) but 2.23-0ubuntu10 is installed
 libcairo-perl : Depends: perlapi-5.18.1 but it is not installable
 libclass-methodmaker-perl : Depends: perlapi-5.18.1 but it is not installable
 libclone-perl : Depends: perlapi-5.18.1 but it is not installable
 libcommon-sense-perl : Depends: perl (< 5.18.3~) but 5.22.1-9ubuntu0.5 is installed
 libcrypt-ssleay-perl : Depends: perlapi-5.18.1 but it is not installable
 libcupsmime1 : Depends: libcups2 (= 1.7.2-0ubuntu1.10) but 2.1.3-4ubuntu0.5 is installed
 libdatetime-perl : Depends: perlapi-5.18.1 but it is not installable
 libfcgi-perl : Depends: perlapi-5.18.1 but it is not installable
 libfile-fcntllock-perl : Depends: perlapi-5.18.1 but it is not installable
 libglib-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-perl : Depends: perlapi-5.18.2 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 libio-pty-perl : Depends: perlapi-5.18.1 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libkcmutils4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkde3support4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkio5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkparts4 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkdeclarative5 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                    Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkdesu5 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkdnssd4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
              Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkemoticons4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libkio5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkfile4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
             Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
             Depends: libkio5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
             Depends: libsolid4 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkidletime4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                 Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkio5 : Depends: libstreamanalyzer0 (>= 0.7.8) but it is not installable
 libknewstuff2-4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkio5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Recommends: kdelibs5-data (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libknewstuff3-4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkio5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Recommends: kdelibs5-data (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkolab0 : Depends: libkolabxml1 but it is not installable
 libkprintutils4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                   Depends: libkparts4 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkpty4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 libkrosscore4 : Depends: libkdecore5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
                 Depends: libkdeui5 (= 4:4.14.16-0ubuntu3.2) but 4:4.13.3-0ubuntu0.5 is installed
 liblist-moreutils-perl : Depends: perlapi-5.18.1 but it is not installable
 liblocale-gettext-perl : PreDepends: perlapi-5.18.1 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.18.2 but it is not installable
 libopenconnect2 : Depends: libproxy1 (>= 0.4.7) but it is not installable
 libossp-uuid-perl : Depends: perlapi-5.18.1 but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libpango-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-util-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-validate-perl : Depends: perlapi-5.18.1 but it is not installable
 libperl5.18 : Depends: perl-base (= 5.18.2-2ubuntu1.6) but 5.22.1-9ubuntu0.5 is installed
 libperlio-gzip-perl : Depends: perlapi-5.18.1 but it is not installable
 libplasma3 : Depends: libkcmutils4 (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
              Depends: libkdnssd4 (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
              Depends: libknewstuff3-4 (= 4:4.13.3-0ubuntu0.5) but 4:4.14.16-0ubuntu3.2 is installed
 libproc-processtable-perl : Depends: perlapi-5.18.1 but it is not installable
 libpurple0 : Depends: perlapi-5.18.2 but it is not installable
 libreoffice-pdfimport : Depends: libpoppler58 (>= 0.41.0) but it is not installed
 libsocket6-perl : Depends: perlapi-5.18.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.18.1 but it is not installable
 libsub-name-perl : Depends: perlapi-5.18.1 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-bidi-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-iconv-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-soundex-perl : Depends: perlapi-5.18.1 but it is not installable
 libtk-tablematrix-perl : Depends: perlapi-5.18.1 but it is not installable
 libunicode-string-perl : Depends: perlapi-5.18.1 but it is not installable
 libxml-libxml-perl : Depends: perlapi-5.18.2 but it is not installable
 libxml-libxslt-perl : Depends: perlapi-5.18.1 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 perl-tk : Depends: perlapi-5.18.1 but it is not installable
 python3-pykde4 : Depends: libkdecore5 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libkdeui5 (>= 4:4.14.9) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libkhtml5 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libkio5 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libkparts4 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libktexteditor4 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libplasma3 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
                  Depends: libsolid4 (>= 4:4.14.2) but 4:4.13.3-0ubuntu0.5 is installed
 vlc-nox : Depends: libgnutls28 (>= 3.2.10-0) but it is not installable
           Recommends: libdvdcss2
E: Unmet dependencies. Try using -f.

```

---

### Post by vpotesil on 2018-07-15
Furthermore, here is the apt update which shows repositories:

```
~$ sudo apt updateHit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://archive.canonical.com/ubuntu xenial InRelease              
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease [107 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [258 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [642 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [586 kB]
Fetched 1 808 kB in 3s (591 kB/s)                         
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1624 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

---

### Post by oldfred on 2018-07-15
Have you run this as suggested in line #4?

You might want to run 'apt-get -f install' to correct these.

---

