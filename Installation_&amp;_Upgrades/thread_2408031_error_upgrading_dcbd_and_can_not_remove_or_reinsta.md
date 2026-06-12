---
title: "error upgrading dcbd and can not remove or reinstall"
date: 2018-12-12
forum: Installation &amp; Upgrades
---

### Post by thomas109 on 2018-12-12
Hi 
having the problem upgrading with dcdb

looks like a half broken install.
but can not configure.

error is with dcbd


apt-get install --reinstall:
```
Setting up dcbd (0.9.19-0ubuntu3) ...insserv: Service network has to be enabled to start service dcbd
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package dcbd (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 dcbd
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


dpkg -s apt dpkg is showing: 
```
Package: apt
Status: install ok installed
Priority: important
Section: admin
Installed-Size: 3350
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.2.29
Replaces: bash-completion (<< 1:2.1-4.2+fakesync1), manpages-it (<< 2.80-4~), manpages-pl (<< 20060617-3~), openjdk-6-jdk (<< 6b24-1.11-0ubuntu1~), sun-java5-jdk (>> 0), sun-java6-jdk (>> 0)
Depends: libapt-pkg5.0 (>= 1.2.29), libc6 (>= 2.15), libgcc1 (>= 1:3.0), libstdc++6 (>= 5.2), init-system-helpers (>= 1.18~), ubuntu-keyring, gpgv | gpgv2, gnupg | gnupg2, adduser
Suggests: aptitude | synaptic | wajig, dpkg-dev (>= 1.17.2), apt-doc, python-apt
Breaks: apt-utils (<< 1.1.3), manpages-it (<< 2.80-4~), manpages-pl (<< 20060617-3~), openjdk-6-jdk (<< 6b24-1.11-0ubuntu1~), sun-java5-jdk (>> 0), sun-java6-jdk (>> 0)
Conffiles:
 /etc/apt/apt.conf.d/01-vendor-ubuntu 5232396660502461fc834c0a1229dbe4
 /etc/apt/apt.conf.d/01autoremove 735050108d38dbf99e933a9f647f6892
 /etc/cron.daily/apt-compat bc4a71cbcaeed4179f25d798257fa980
 /etc/kernel/postinst.d/apt-auto-removal 8ad76ae4492b54f0dcbf18c79429dfab
 /etc/logrotate.d/apt 179f2ed4f85cbaca12fa3d69c2a4a1c3
Description: commandline package manager
 This package provides commandline tools for searching and
 managing as well as querying information about packages
 as a low-level access to all features of the libapt-pkg library.
 .
 These include:
  * apt-get for retrieval of packages and information about them
    from authenticated sources and for installation, upgrade and
    removal of packages together with their dependencies
  * apt-cache for querying available information about installed
    as well as installable packages
  * apt-cdrom to use removable media as a source for packages
  * apt-config as an interface to the configuration settings
  * apt-key as an interface to manage authentication keys
Original-Maintainer: APT Development Team <deity@lists.debian.org>


Package: dpkg
Essential: yes
Status: install ok installed
Priority: required
Section: admin
Installed-Size: 6655
Origin: debian
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Bugs: debbugs://bugs.debian.org
Architecture: amd64
Multi-Arch: foreign
Version: 1.18.4ubuntu1.5
Replaces: manpages-it (<< 2.80-4)
Pre-Depends: libbz2-1.0, libc6 (>= 2.14), liblzma5 (>= 5.1.1alpha+20120614), libselinux1 (>= 2.3), zlib1g (>= 1:1.1.4), tar (>= 1.23)
Suggests: apt
Breaks: apt (<< 0.7.7~), apt-cudf (<< 3.3~beta1-3~), aptitude (<< 0.4.7-1~), auctex (<< 11.87-3+deb8u1~), ccache (<< 3.1.10-1~), cups (<< 1.7.5-10~), dbus (<< 1.8.12-1ubuntu6~), debian-security-support (<< 2014.10.26~), distcc (<< 3.1-6.1~), doc-base (<< 0.10.5~), dpkg-dev (<< 1.15.8), fontconfig (<< 2.11.1-0ubuntu5~), fusionforge-plugin-mediawiki (<< 5.3.2+20141104-3~), gap-core (<< 4r7p5-2~), gitweb (<< 1:2.1.4-2.1~), grace (<< 1:5.1.24-3~), gxine (<< 0.5.908-3.1~), hoogle (<< 4.2.33-4~), icecc (<< 1.0.1-2~), install-info (<< 5.1.dfsg.1-3~), libapache2-mod-php5 (<< 5.6.4+dfsg-3~), libapache2-mod-php5filter (<< 5.6.4+dfsg-3~), libdpkg-perl (<< 1.15.8), libjs-protoaculous (<< 5~), man-db (<< 2.6.3-6~), mcollective (<< 2.6.0+dfsg-2.1~), php5-fpm (<< 5.6.4+dfsg-3~), pypy (<< 2.4.0+dfsg-3~), readahead-fedora (<< 2:1.5.6-5.2~), software-center (<< 13.10-0ubuntu9~), ufw (<< 0.35-0ubuntu2~), ureadahead (<< 0.100.0-17~), wordpress (<< 4.1+dfsg-1~), xfonts-traditional (<< 1.7~), xine-ui (<< 0.99.9-1.2~)
Conflicts: ada-reference-manual (<< 20021112web-4~), asn1-mode (<< 2.7-7~), bogosort (<< 0.4.2-3~), cl-yacc (<< 0.3-3~), cpp-4.1-doc (<< 4.1.2.nf2-4~), cpp-4.2-doc (<< 4.2.4.nf1-4~), gcc-4.1-doc (<< 4.1.2.nf2-4~), gcc-4.2-doc (<< 4.2.4.nf1-4~), gcj-4.1-doc (<< 4.1.2.nf2-4~), gcj-4.2-doc (<< 4.2.4.nf1-4~), gfortran-4.1-doc (<< 4.1.2.nf2-4~), gfortran-4.2-doc (<< 4.2.4.nf1-4~), ggz-docs (<< 0.0.14.1-2~), glame (<< 2.0.1-6~), gnat-4.1-doc (<< 4.1.2.nf2-4~), gnat-4.2-doc (<< 4.2.4.nf1-4~), gtalk (<< 0.99.10-16~), libalogg-dev (<< 1.3.7-2~), libgtk1.2-doc (<< 1.2.10-19~), libnettle-dev (<< 2~), liborbit-dev (<< 0.5.17-12~), libreadline5-dev (<< 5.2-8~), librep-doc (<< 0.90~), mmucl (<< 1.5.2-3~), nxml-mode (<< 20041004-9~), octave3.0-info (<< 1:3.0.5-7+rm), octave3.2-info (<< 3.2.4-12+rm), polgen-doc (<< 1.3-3+rm), r6rs-doc (<< 1.0-2~), serveez-doc (<< 0.1.5-3~), slat (<< 2.0-6~), texlive-base-bin-doc (<< 2007.dfsg.2-9~), ttcn-el (<< 0.6.9-2~), ulog-acctd (<< 0.4.3-3~), xconq-doc (<< 7.4.1-5~), zenirc (<< 2.112.dfsg-1~)
Conffiles:
 /etc/alternatives/README 69c4ba7f08363e998e0f2e244a04f881
 /etc/cron.daily/dpkg b8065b6bfc248caba501c3f5bb508e66
 /etc/dpkg/dpkg.cfg f4413ffb515f8f753624ae3bb365b81b
 /etc/logrotate.d/dpkg 782ea5ae536f67ff51dc8c3e2eeb4cf9
Description: Debian package management system
 This package provides the low-level infrastructure for handling the
 installation and removal of Debian software packages.
 .
 For Debian package development tools, install dpkg-dev.
Homepage: https://wiki.debian.org/Teams/Dpkg
Original-Maintainer: Dpkg Developers <debian-dpkg@lists.debian.org>



```


thanks for checking T

---

