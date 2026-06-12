---
title: "Kubuntu Package Problem"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Redscare on 2007-05-11
Please help!!! I have removed some kubuntu-desktop included applications in the past, and hence have removed the kubuntu-desktop metapackage. I believe that this is what caused this message on sudo apt-get autoremove:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkonq4-dev libconvert-binhex-perl libattr1-dev
  libsoap-lite-perl kdelibs4-dev ktip libnet-xmpp-perl
  libaspell-dev kspy kdesdk-kio-plugins libneon26 libaudio-dev
  libuser-perl libcrypt-ssleay-perl liblockdev1 libnet-ssleay-perl
  kdebase comerr-dev libpcre3-dev kpager kapptemplate
  liblualib50-dev kde-core latex-xft-fonts qca-tls libapr1
  libxmu-headers mesa-common-dev libkexiv2-0 subversion
  koffice-data libkrb5-dev qt3-dev-tools libsasl2-dev libogg-dev
  libjasper-1.701-dev libossp-uuid-perl libqt3-compat-headers
  libpcrecpp0 libossp-uuid15 libsvn1 kdesdk-kfile-plugins valgrind
  liblua50-dev libnet-jabber-perl lua50 libjasper-runtime
  libavahi-qt3-dev python-imaging libacl1-dev qt3-designer
  libglu1-mesa-dev libqt3-mt-dev libmikmod2 hspell
  libio-stringy-perl libxslt1-dev libssl-dev libxt-dev libxmu-dev
  kdebase-dev libnet-google-perl kbugbuster python-feedparser
  libauthen-sasl-perl hddtemp kcachegrind libtiff4-dev
  libxml-stream-perl libwww-search-perl libmime-perl libqt3-headers
  libmime-lite-perl libasound2-dev libtiffxx0c2 libgl1-mesa-dev
  liblcms1-dev libfcgi-perl libkadm55 poxml xmms qobex kompare
  libjcode-pm-perl kdelibs kunittest kappfinder
  libio-socket-ssl-perl libartsc0-dev libopenexr-dev kdesdk-misc
  koffice-libs libmng-dev python-chardet python-xmms kdesdk-scripts
  libcupsys2-dev libaprutil1 libvorbis-dev gettext-kde kuiviewer
  libidn11-dev libbz2-dev libopenobex1 libdigest-sha1-perl
  libarts1-dev kmtrace
The following packages will be REMOVED:
  comerr-dev gettext-kde hddtemp hspell kappfinder kapptemplate
  kbugbuster kcachegrind kde-core kdebase kdebase-dev kdelibs
  kdelibs4-dev kdesdk-kfile-plugins kdesdk-kio-plugins kdesdk-misc
  kdesdk-scripts kmtrace koffice-data koffice-libs kompare kpager
  kspy ktip kuiviewer kunittest latex-xft-fonts libacl1-dev libapr1
  libaprutil1 libarts1-dev libartsc0-dev libasound2-dev
  libaspell-dev libattr1-dev libaudio-dev libauthen-sasl-perl
  libavahi-qt3-dev libbz2-dev libconvert-binhex-perl
  libcrypt-ssleay-perl libcupsys2-dev libdigest-sha1-perl
  libfcgi-perl libgl1-mesa-dev libglu1-mesa-dev libidn11-dev
  libio-socket-ssl-perl libio-stringy-perl libjasper-1.701-dev
  libjasper-runtime libjcode-pm-perl libkadm55 libkexiv2-0
  libkonq4-dev libkrb5-dev liblcms1-dev liblockdev1 liblua50-dev
  liblualib50-dev libmikmod2 libmime-lite-perl libmime-perl
  libmng-dev libneon26 libnet-google-perl libnet-jabber-perl
  libnet-ssleay-perl libnet-xmpp-perl libogg-dev libopenexr-dev
  libopenobex1 libossp-uuid-perl libossp-uuid15 libpcre3-dev
  libpcrecpp0 libqt3-compat-headers libqt3-headers libqt3-mt-dev
  libsasl2-dev libsoap-lite-perl libssl-dev libsvn1 libtiff4-dev
  libtiffxx0c2 libuser-perl libvorbis-dev libwww-search-perl
  libxml-stream-perl libxmu-dev libxmu-headers libxslt1-dev
  libxt-dev lua50 mesa-common-dev poxml python-chardet
  python-feedparser python-imaging python-xmms qca-tls qobex
  qt3-designer qt3-dev-tools subversion valgrind xmms
0 upgraded, 0 newly installed, 107 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 145MB disk space will be freed.
Do you want to continue [Y/n]?     
```
It seems that apt-get autoremove is removing the rest of kubuntu-desktop. Is there any way to fix this without removing/reinstalling kde?

---

### Post by mihail on 2007-05-17
I had the same problem, and actually you helped me to solve it, so thanks Redscare :)
I installed kubuntu-desktop: ```
sudo apt-get install kubuntu-desktop
```and after that apt-get won't try to remove some of my necessary and still used packages.

On the other hand of course, kubuntu-desktop package installed ~22MB of packages that I really don't need, but at least my apt-get is working properly now.

---

### Post by Redscare on 2007-05-17
Thanks for the advice, but space is precious, I'd rather find another solution.

---

